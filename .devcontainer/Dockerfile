# base image
FROM ubuntu:20.04

ARG USERNAME=tuffix
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y \
    wget \
    curl \
    nano \
    apt-utils \
    iproute2 \
    cron \
    run-one \
    redis \
    git \
    python3-pip \
    ruby-foreman \
    sqlite3 \
    httpie \
    jq \
    #/usr/share/dict/words
    wamerican \
    # download and run tuffix install script
    && wget https://csufcs.com/tuffixize -O - | bash \
    && rm -rf /var/lib/apt/lists/*

# Python dependencies
RUN ln -s /usr/bin/python3 /usr/bin/python \
    && python -m pip install \
    fastapi[all] \
    sqlite-utils \
    pyinstaller \
    httpx

RUN mkdir /home/projects

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    #
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    # add username to crontab usergroup
    && adduser $USERNAME crontab

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $USERNAME

WORKDIR /home/projects

CMD [ "/bin/bash" ]
