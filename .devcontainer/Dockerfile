FROM ubuntu:latest

ARG NVM_NODE_VERSION=22
ARG PYENV_PYTHON_VERSION=3.13

ENV HOME='/root'
ENV NVM_NODE_VERSION=${NVM_NODE_VERSION}
ENV PYENV_PYTHON_VERSION=${PYENV_PYTHON_VERSION}

SHELL ["/bin/bash", "-c"]

# Install dependencies
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y git curl 

# Install python
RUN curl -fsSL https://pyenv.run | bash 
RUN echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
RUN echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
RUN echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
RUN echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
RUN echo 'eval "$(pyenv init - bash)"' >> ~/.profile
RUN apt-get install -y build-essential libssl-dev zlib1g-dev libbz2-dev \
    libreadline-dev libsqlite3-dev libncursesw5-dev xz-utils tk-dev \
    libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

ENV PYENV_ROOT="$HOME/.pyenv"
ENV PATH="$PYENV_ROOT/bin:$PATH"

RUN pyenv install $PYENV_PYTHON_VERSION
RUN pyenv global $PYENV_PYTHON_VERSION

# Install NVM
RUN curl -fsSL https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash

RUN export NVM_DIR="$HOME/.nvm" && \
    . "$NVM_DIR/nvm.sh" && \
    nvm install $NVM_NODE_VERSION && \
    nvm use $NVM_NODE_VERSION

# Cleanup to reduce image size
RUN rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY . .
