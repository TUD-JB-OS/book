# GitLab and TU server

requirements
runner
linux website

keys
variables


.gitlab-ci.yml
```{bash}
stages:
  - deploy

image: python:3.11-slim

variables:
  SSH_COMMAND: 'ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null -o IdentitiesOnly=yes'
  LOCAL_BUILD_DIR: "_build/html"
  HOST: "127.0.0.1"
  BASE_URL: ""
  
before_script:
  - apt-get update
  - apt-get install -y --no-install-recommends curl rsync openssh-client git

  # Node.js (MyST tooling kan node nodig hebben)
  - curl -fsSL https://deb.nodesource.com/setup_20.x | bash -
  - apt-get install -y --no-install-recommends nodejs
  - node --version
  - npm --version

  # Python deps
  - python -m pip install --upgrade pip
  - pip install mystmd

  # SSH key laden
  - eval "$(ssh-agent -s)"
  - chmod 400 "$WEBSITE_UPLOAD_KEY"
  - ssh-add "$WEBSITE_UPLOAD_KEY"

deploy:
  stage: deploy
  script:
    # Build (belangrijk: geef het projectpad mee)
    - myst build --html 
   
    - rsync -ravz "${LOCAL_BUILD_DIR}/" -e "${SSH_COMMAND} -i ${WEBSITE_UPLOAD_KEY}" "${DEPLOY_USER}@${DEPLOY_HOST}:${DEPLOY_PATH}/"
```

