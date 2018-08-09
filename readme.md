# devops-toolbox
The sandbox environment for devops & automation running in docker container. 

These are batteries included
* git
* ansible
* gcloud
* terraform
* oh-my-zsh


## Installation

- Download into local directory
- Make a copy of `.env.example` and rename file to `.env`
- Update your local configuration of environment 

```ini
# Workspace Path
# The path that points to your workspace, will be available at `/workspace`.
# This is the relative path from current direcotry to your workspace 

WORKSPACE=../..

# Workspace
GIT_USERNAME=username
GIT_EMAIL=username@gmail.com

```

- Just run this command to get toolbox up and running

``` bash
docker-compose up -d
```



