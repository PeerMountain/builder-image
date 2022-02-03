FROM openjdk:11

RUN apt-get update
RUN apt-get install npm -y
RUN apt-get install apt-transport-https
RUN sh -c 'wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
RUN sh -c 'wget -qO- https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
RUN apt-get update
RUN apt-get install dart
RUN curl -L get.web3j.io | sh && . ~/.web3j/source.sh

RUN apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release -y
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
RUN echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt-get install docker-ce docker-ce-cli containerd.io

ENV PATH="/usr/lib/dart/bin:${PATH}"

RUN dart pub global activate protoc_plugin
ENV PATH="/root/.pub-cache/bin/protoc-gen-dart:${PATH}"
