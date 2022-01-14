## set up github - one time only (for osx)

step 1: Register for github

step 2: Run following commands in terminal

ssh-keygen -t ed25519 -C "your_email@example.com"
eval "$(ssh-agent -s)"
open ~/.ssh/config

step 3: copy following to opened file

Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519


## first time

git clone git@github.com:mukundraj/ml-portal.git
cd ml-portal
docker-compose -f docker-compose.yml -f docker-compose-prod.yml up -d --build


## to pull portal updates

docker-compose -f docker-compose.yml -f docker-compose-prod.yml down
git pull
docker-compose -f docker-compose.yml -f docker-compose-prod.yml up -d --build

## to start and stop portal for routine analysis

docker-compose start
docker-compose stop
