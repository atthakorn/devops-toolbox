
FROM ubuntu:16.04
LABEL maintainer="atthakorn@shareinvestor.com"

# get rid of debian error 
ARG DEBIAN_FRONTEND=noninteractive

# update & upgrade repository
RUN apt-get update && apt-get upgrade -y


# install common packages
RUN apt-get install -y \
        build-essential \
        gcc \
        libssl-dev \
        libffi-dev \
        libxml2-dev \
        libxslt1-dev \
        zlib1g-dev \
        python-dev \
        python-novaclient \
        python-neutronclient \
        python-pip \
        ca-certificates \
        openssl \
        command-not-found

        

# install utility
RUN apt-get install -y \
        zsh \
        wget  \
        curl \
        man \
        dos2unix \
        zip \
        nmap \
        tree 



# git
ARG GIT_USERNAME
ARG GIT_EMAIL

RUN  apt-get install -y git git-extras \
      && git config --global user.name ${GIT_USERNAME} \
      && git config --global user.email ${GIT_EMAIL} 




# ansible
ARG ANSIBLE_VERSION=2.4.2.0-1ppa~xenial

RUN  apt-get install -y software-properties-common \
      && apt-add-repository ppa:ansible/ansible \
      && apt-get update \
      && apt-get install -y ansible=${ANSIBLE_VERSION}


# terraform
ARG TERRAFORM_VERSION=0.11.1
ARG TERRAFORM_DOWNLOAD_URL=https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip
RUN wget $TERRAFORM_DOWNLOAD_URL -O terraform.zip \
        && unzip terraform.zip -d /usr/local/bin \
        && rm terraform.zip


# gcloud
RUN export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)" \
        && echo "deb http://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" |  tee -a /etc/apt/sources.list.d/google-cloud-sdk.list \
        && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - \
        && apt-get update \
        && apt-get install -y google-cloud-sdk kubectl


# install oh-my-zsh
RUN curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh || true

# push oh-my-zsh setting
COPY .zshrc /root/.zshrc
RUN dos2unix /root/.zshrc




# workdir
WORKDIR /workspace
