FROM ubuntu:20.04

WORKDIR /root
ARG ANDROID_SDK_ROOT=/usr/lib/android-sdk
ARG HOST_OS=linux
ARG HOST_OS_SHORT=linux
ARG SDK_VER=8512546_latest
ARG SDK_API_LEVEL=29
ARG SDK_BUILD_TOOLS=29.0.3

RUN apt update && apt install -y curl zip unzip android-sdk
RUN \
curl https://dl.google.com/android/repository/commandlinetools-${HOST_OS_SHORT}-${SDK_VER}.zip -L --output /root/asdk.zip && \
unzip /root/asdk.zip -d ${ANDROID_SDK_ROOT}/cmdline-tools && rm -rf /root/asdk.zip && mv ${ANDROID_SDK_ROOT}/cmdline-tools/cmdline-tools ${ANDROID_SDK_ROOT}/cmdline-tools/latest

RUN yes | ${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager --licenses && \
${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager "platform-tools" "platforms;android-${SDK_API_LEVEL}" "build-tools;${SDK_BUILD_TOOLS}"
RUN ${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager ndk-bundle
