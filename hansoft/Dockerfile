FROM ubuntu:bionic
LABEL maintainer "ueno.s <ueno.s@gamestudio.co.jp>"

ARG USER=hansoft
ARG PASSWD=hansoft

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
RUN apt-get update && apt-get -y install wget gnupg less language-pack-ja-base language-pack-ja tzdata curl jq git openssl sudo vim libxcb-xinput0 libgles2-mesa unzip wget

RUN echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc ;\
    echo 'export LANGUAGE="ja_JP:ja"' >> ~/.bashrc

RUN wget -P /opt 'https://cache.hansoft.com/Hansoft+Server+11.0030+Linux2.6+x64.zip' \
    && unzip /opt/Hansoft+Server+11.0030+Linux2.6+x64.zip -d /opt/

RUN mkdir -p /opt/hpmweb \
    && wget -P /opt/hpmweb 'https://cache.hansoft.com/HPMWeb-Linux-x64-11.0016.zip' \
    && unzip /opt/hpmweb/HPMWeb-Linux-x64-11.0016.zip -d /opt/hpmweb

RUN sudo update-alternatives --set editor /usr/bin/vim.basic \
    && useradd -m $USER \
    && echo "$USER:$PASSWD" | chpasswd \
    && echo "$USER ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
