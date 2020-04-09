FROM ubuntu:18.04

# install linux command & java8 & cli-editor
RUN apt-get update
RUN apt-get install -y git
RUN apt install -y curl
RUN apt install -y openjdk-8-jdk
RUN git clone https://github.com/TomoyukiNamura/cli-editor.git /tmp/cli-editor
WORKDIR /tmp/cli-editor
RUN bash install.sh
RUN bash update.sh

# install digdag
RUN curl -o ~/bin/digdag --create-dirs -L "https://dl.digdag.io/digdag-latest"
RUN chmod +x ~/bin/digdag
RUN echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc

# install embulk
RUN curl --create-dirs -o ~/.embulk/bin/embulk -L "https://dl.embulk.org/embulk-latest.jar"
RUN chmod +x ~/.embulk/bin/embulk
RUN echo 'export PATH="$HOME/.embulk/bin:$PATH"' >> ~/.bashrc

# install embulk plugin
ENV PATH="/root/.embulk/bin:$PATH"
RUN embulk gem install embulk-output-mysql

# change workdir
WORKDIR /home
