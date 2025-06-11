FROM ubuntu:24.04

LABEL mainteiner="joaodanilo19922@gmail.com"
LABEL version="0.1"
LABEL description="Ambiente de programação para o curso.dev"

WORKDIR "/workspace"

RUN mkdir /apps/

RUN apt-get update

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y tzdata

RUN apt-get install -y  curl git ca-certificates postgresql-client locales

# Instalação do nvm | nodejs | npm (versão: lts/hydrogen)
ENV NODE_VERSION=18.14.2
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
ENV NVM_DIR=/root/.nvm
RUN . "$NVM_DIR/nvm.sh" && nvm install ${NODE_VERSION}
RUN . "$NVM_DIR/nvm.sh" && nvm use v${NODE_VERSION}
RUN . "$NVM_DIR/nvm.sh" && nvm alias default v${NODE_VERSION}
ENV PATH="/root/.nvm/versions/node/v${NODE_VERSION}/bin/:${PATH}"

# Instalação do neo vim
#RUN cd /apps/ && curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux-x86_64.tar.gz
#RUN cd /apps/ && tar xvzf nvim-linux-x86_64.tar.gz && rm nvim-linux-x86_64.tar.gz
#ENV PATH="$PATH:/apps/nvim-linux-x86_64/bin"
#RUN mkdir -p /root/.config/nvim/
#COPY init.lua /root/.config/nvim/

# Instalação docker
RUN apt-get update
RUN install -m 0755 -d /etc/apt/keyrings
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
RUN chmod a+r /etc/apt/keyrings/docker.asc
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt-get update
RUN apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
RUN locale-gen en_US.UTF-8