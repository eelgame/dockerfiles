FROM ubuntu:20.04

RUN apt-get update \
    && apt-get install --no-install-recommends -y postgresql-server-dev-all \
    && apt-get install --no-install-recommends --no-install-suggests -y curl ca-certificates \
    && apt-get install -y libpq-dev \
    && apt-get install -y zlib1g-dev libtinfo-dev \
    && curl -sSL https://get.haskellstack.org/ | sh \
    && apt clean && rm -rf /var/lib/apt/lists/*

# Set locale
ENV LANG C.UTF-8
