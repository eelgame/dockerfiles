FROM ubuntu:20.04

# RUN sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list

RUN groupadd glot
RUN apt update
RUN apt install -y dirmngr gnupg apt-transport-https ca-certificates software-properties-common
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
RUN apt-add-repository 'deb https://download.mono-project.com/repo/ubuntu stable-focal main'
RUN apt update
RUN apt install -y mono-complete
RUN mono --version