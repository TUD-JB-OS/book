# GitLab and TU server

requirements
- runner
- linux website
or
- gl pages

keys
variables

https://gitlab.com/pages/jupyterbook

This 

```{code} yml 
:caption: .gitlab-ci.yml for TU server deployment

stages:
  - deploy

image: python:3.11-slim

variables:
  SSH_COMMAND: 'ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null -o IdentitiesOnly=yes'
  LOCAL_BUILD_DIR: "_build/html"
  HOST: "127.0.0.1"             # prevents running local host resulting in an error
  BASE_URL: ""                  # specify the base url, e.g. the folder from root
  
before_script:
  - apt-get update
  - apt-get install -y --no-install-recommends curl rsync openssh-client git

  # Node.js
  - curl -fsSL https://deb.nodesource.com/setup_20.x | bash -
  - apt-get install -y --no-install-recommends nodejs
  - node --version
  - npm --version

  # Python deps
  - python -m pip install --upgrade pip
  - pip install mystmd
  - pip install -r requirements.txt

  # SSH key laden
  - eval "$(ssh-agent -s)"
  - chmod 400 "$WEBSITE_UPLOAD_KEY"
  - ssh-add "$WEBSITE_UPLOAD_KEY"

deploy:
  stage: deploy
  script:
    # builds the book
    - myst build --html 
    
    # syncs with the server
    - rsync -ravz "${LOCAL_BUILD_DIR}/" -e "${SSH_COMMAND} -i ${WEBSITE_UPLOAD_KEY}" "${DEPLOY_USER}@${DEPLOY_HOST}:${DEPLOY_PATH}/"
```

other option (from Anton):

```{code} yml
default:
  image:
    name: ghcr.io/prefix-dev/pixi
  cache:
    key: "$CI_JOB_NAME"
    paths:
      - .pixi
      - _build
  before_script:
    - eval $(pixi shell-hook --shell bash)
    - pixi global install git
    - git config --global --add safe.directory $CI_PROJECT_DIR
    - pixi install
    - eval "$(pixi run ssh-agent -s)"
    - chmod 400 "$WEBSITE_UPLOAD_KEY"
    - pixi run ssh-add "$WEBSITE_UPLOAD_KEY" >/dev/null

variables:
  FF_USE_FASTZIP: "true"
  CACHE_COMPRESSION_LEVEL: "fastest"
  SSH_COMMAND: "ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no"
  JUPYTER_NUM_PROCS: "10"
  HOST: "127.0.0.1"  # Needed to avoid binding to ::1.

workflow:
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
      variables:
        BASE_URL: "/branch_${CI_COMMIT_REF_SLUG}"
    - if: '$CI_COMMIT_BRANCH == "master"'
    - when: never

build branch website:
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
  variables:
    WEBSITE_UPLOAD_PATH: /branch_${CI_COMMIT_REF_SLUG}
  environment:
    name: branch/$CI_COMMIT_REF_SLUG
    on_stop: stop branch website
    url: https://topocondmat.org/branch_${CI_COMMIT_REF_SLUG}/
  script:
    - pixi run postprocess-html
    - pixi run rsync -ravz _build/html/ -e "$SSH_COMMAND" uploader@tnw-qn1.tudelft.net:$WEBSITE_UPLOAD_PATH

build main website:
  only:
    - master@qt/topocm
  variables:
    WEBSITE_UPLOAD_PATH: /
  environment:
    name: published
    url: https://topocondmat.org/
  script:
    - pixi run postprocess-html
    - pixi run rsync -ravz _build/html/ -e "$SSH_COMMAND" uploader@tnw-qn1.tudelft.net:$WEBSITE_UPLOAD_PATH

stop branch website:
  needs:
    - build branch website
  script:
    - mkdir -p /tmp/empty_dir
    - pixi run rsync -av --delete /tmp/empty_dir/ -e "$SSH_COMMAND" uploader@tnw-qn1.tudelft.net:$WEBSITE_UPLOAD_PATH/
  when: manual
  environment:
    name: branch/$CI_COMMIT_REF_SLUG
    action: stop
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
      when: manual
  variables:
    WEBSITE_UPLOAD_PATH: /branch_${CI_COMMIT_REF_SLUG}
  allow_failure: true


```