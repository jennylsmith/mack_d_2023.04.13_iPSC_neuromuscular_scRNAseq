FROM rocker/r-ver:4.4

# FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04
ENV RENV_VER='1.0.11'

# update packages and install dependencies
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    build-essential gfortran \
    zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev \
    libssl-dev libreadline-dev libffi-dev \
    wget xorg openbox git gh

RUN apt-get -y install pkg-config python3-venv python3-dev

# install R package renv
# See Ubuntu repos for more packages that can be installed through apt manager: https://cloud.r-project.org/bin/linux/ubuntu/
RUN Rscript -e "install.packages('remotes', repos='https://cloud.r-project.org', verbose='TRUE'); remotes::install_version('renv', version = '$RENV_VER', verbose = 'TRUE')"

# required for the VSCode R Extension. See https://github.com/REditorSupport/vscode-R/wiki
RUN Rscript -e "install.packages('languageserver')"