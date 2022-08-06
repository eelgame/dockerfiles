FROM ubuntu:20.04

WORKDIR /root
ARG NDK_VER=r23c
ARG ANDROID_SDK_ROOT=/usr/lib/android-sdk
ARG HOST_OS=linux
ARG HOST_OS_SHORT=linux
ARG SDK_VER=8512546_latest
ARG SDK_API_LEVEL=29
ARG SDK_BUILD_TOOLS=29.0.3

RUN apt update && apt install -y curl zip unzip android-sdk cmake
RUN apt install -y locales
RUN locale-gen en_US.UTF-8
RUN dpkg-reconfigure locales
RUN apt install -y python3 python3-pip
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 1
RUN \
curl https://dl.google.com/android/repository/commandlinetools-${HOST_OS_SHORT}-${SDK_VER}.zip -L --output /root/asdk.zip && \
unzip /root/asdk.zip -d ${ANDROID_SDK_ROOT}/cmdline-tools && rm -rf /root/asdk.zip && mv ${ANDROID_SDK_ROOT}/cmdline-tools/cmdline-tools ${ANDROID_SDK_ROOT}/cmdline-tools/latest

RUN yes | ${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager --licenses && \
${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager "platform-tools" "platforms;android-${SDK_API_LEVEL}" "build-tools;${SDK_BUILD_TOOLS}"
RUN ${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager ndk-bundle
RUN export ANDROID_NDK_ROOT=/root/android-ndk-${NDK_VER} && curl https://dl.google.com/android/repository/android-ndk-${NDK_VER}-${HOST_OS}.zip -L --output /root/andk.zip && unzip /root/andk.zip -d $(dirname ${ANDROID_NDK_ROOT}) && rm -rf /root/andk.zip
