## set up github - one time only (for osx)

step 1: Register for github

step 2: Run following commands in terminal

ssh-keygen -t ed25519 -C "your_email@example.com"
eval "$(ssh-agent -s)"
open ~/.ssh/config

step 3: copy following text to open config file, then save and exit editor.

  Host *
    AddKeysToAgent yes
    UseKeychain yes
    IdentityFile ~/.ssh/id_ed25519


## to set up portal locally for the first time

step 1: run following commands in terminal

  git clone git@github.com:mukundraj/ml-portal.git
  cd ml-portal
  docker-compose -f docker-compose.yml -f docker-compose-prod.yml up -d --build

step 2: go to following path in web browser

  localhost:8080

## to pull portal updates

step 1: run following commands in terminal

  docker-compose -f docker-compose.yml -f docker-compose-prod.yml down
  git pull
  docker-compose -f docker-compose.yml -f docker-compose-prod.yml up -d --build

step 2: go to following path in web browser to test updates

  localhost:8080

step 3: stop container after analysis by typing following command into terminal

  docker-compose stop

## to start and stop portal for routine analysis

  docker-compose start
  docker-compose stop
