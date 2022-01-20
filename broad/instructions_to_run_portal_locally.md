## install docker client and set up github - one time only (osx instructions here)

**step 1** Download and install docker client

**step 2:** Register for github

**step 3:** Run following commands in terminal

    ssh-keygen -t ed25519 -C "your_email@example.com"
    eval "$(ssh-agent -s)"
    open ~/.ssh/config

**step 4:** copy following text to open config file, then save and exit editor.

    Host *
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/id_ed25519

**step 5** copy the public key to clipbord

    pbcopy < ~/.ssh/id_ed25519.pub

**step 6** provide public key to github using following instructions - https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

**step 7** install xcode if not installed

## to set up portal locally for the first time

**step 1**: run following commands in terminal

    git clone git@github.com:mukundraj/ml-portal.git
    cd ml-portal
    docker-compose -f docker-compose.yml -f docker-compose-prod.yml up -d --build

**step 2:** go to following path in web browser

  localhost:8080

## to pull portal updates

**step 1:** run following commands in terminal

    docker-compose -f docker-compose.yml -f docker-compose-prod.yml down
    git pull
    docker-compose -f docker-compose.yml -f docker-compose-prod.yml up -d --build

**step 2:** go to following path in web browser to test updates

    localhost:8080

**step 3:** stop container after analysis by typing following command into terminal

    docker-compose stop

## to start and stop portal for routine analysis

    docker-compose start
    docker-compose stop
