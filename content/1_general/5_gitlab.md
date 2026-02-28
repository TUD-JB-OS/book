# GitLab and TU server

requirements
runner
linux website

keys
variables




```{yml} .gitlab-ci.yml
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

