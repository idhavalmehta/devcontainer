FROM debian:latest

ARG NVM_NODE_VERSION=22
ARG PYENV_PYTHON_VERSION=3.13.2

ENV NVM_NODE_VERSION=${NVM_NODE_VERSION}
ENV PYENV_PYTHON_VERSION=${PYENV_PYTHON_VERSION}

SHELL ["/bin/bash", "-c"]

RUN apt-get update
RUN apt-get upgrade -y

COPY ./install /root/install
RUN chmod -R +x /root/install
RUN . /root/install/install-git.sh
RUN . /root/install/install-node.sh

RUN rm -rf /var/lib/apt/lists/*
