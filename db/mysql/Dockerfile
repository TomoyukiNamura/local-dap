FROM mysql:5.7

# install linux command & cli-editor
RUN apt update
RUN apt install -y git locales-all
RUN git clone https://github.com/TomoyukiNamura/cli-editor.git /tmp/cli-editor
WORKDIR /tmp/cli-editor
RUN bash install.sh
RUN bash update.sh

# add utf8 setting to mysql
RUN echo '[mysqld]' >> /etc/mysql/my.cnf
RUN echo 'character-set-server=utf8' >> /etc/mysql/my.cnf
RUN echo '[client]' >> /etc/mysql/my.cnf
RUN echo 'default-character-set=utf8' >> /etc/mysql/my.cnf

# change workdir
WORKDIR /home
