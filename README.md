
<!-- README.md is generated from README.Rmd. Please edit that file -->

# bologna

Bologna is a [Docker](https://www.docker.com/) image for
programmatically building educational content.

## Getting Started

1.  Install [Docker](https://docs.docker.com/install/).
2.  Start Docker.
3.  Run `docker pull seankross/bologna`
4.  Run `docker run -dp 8787:8787 -e ROOT=TRUE seankross/bologna`
5.  Navigate to <http://localhost:8787/> in your web browser.

## Getting Started on Digital Ocean

See all the instructions with pictures here:
<https://www.digitalocean.com/community/tutorials/how-to-use-the-digitalocean-docker-application>

Throughout I will call the IP address `YOURIP`.

1.  Make sure you use Under Choose an image, select the One-click apps
    tab to create a Docker image. Don’t forget to add your SSH keys.
2.  Run `ssh root@YOURIP` in a Terminal to log into the machine.
3.  Start on `docker pull` test below.
4.  Run `docker pull seankross/bologna`
5.  To start the RStudio server `docker run -dp 8787:8787 -e ROOT=TRUE
    seankross/bologna`. Go to `YOURIP:8787`.
6.  To run on the Terminal, run `docker run -it -e ROOT=TRUE
    seankross/bologna bash`

Now you are in the Docker image and you can run `R`.

### Setting up some defaults

NB: `git` is already installed on the machine but not configured

1.  Either `ssh ~/.gitconfig root@YOURIP:~/` or set up `git config
    --global user.name "GITHUB_USERNAME"` and additional instructions
    here:
    <https://help.github.com/articles/setting-your-username-in-git/>
2.  Create a new GitHub [Personal Auth
    Token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)
    that has permissions to push/pull on private repos for `CDS` so you
    don’t need passwords for `git pull`. NB: If you have 2-factor
    authentication, [you use your PAT, not your password when
    prompted.](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#using-a-token-on-the-command-line)

### Google Authentication Tokens

Read
<https://cran.r-project.org/web/packages/googlesheets/vignettes/managing-auth-tokens.html>
to talk about OAuth Tokens.

1.  Create a `googlesheets_token.rds` or the like with your
    authentication if necessary.

2.  OAuth is a problem for now. Try `googlesheets::drive_auth()`. If you
    get `sh: 1: xdg-open: not found`, then run in `bash`: `sudo apt-get
    install xdg-utils --fix-missing` and rerun. The command may now give
    you a link to open in your (non-DO, non-Docker) browser. Paste the
    authentication code.

3.  
### A little docker commands

See
<https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes>

1.  See the volumes made `docker volume ls` if you want to stop a
    running image.
2.  See the running containers `docker ps`. This will show you how the
    are ports are mapped.
3.  If you are aggressive, you can try `docker system prune` for
    removing all stopped things.
