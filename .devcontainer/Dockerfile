# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.192.0/containers/dotnet/.devcontainer/base.Dockerfile

# [Choice] .NET version: 3.10
ARG VARIANT="3.10"
FROM mcr.microsoft.com/devcontainers/python:0-${VARIANT}

# Set up machine requirements to build the repo
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends curl git

# install azure functions core tools v4
# https://github.com/Azure/azure-functions-core-tools#debian-9--10
# DEBIAN_VERSION=11
RUN wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg\
    && sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/ \
    && wget -q https://packages.microsoft.com/config/debian/11/prod.list \
    && sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list \
    && sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg \
    && sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list \
    && echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections \
    && sudo apt-get update \
    && sudo apt-get -y install azure-functions-core-tools-4