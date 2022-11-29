ARG uid=1000
ARG gid=1000
ARG deno_version=v1.28.2

FROM debian:bullseye

ARG gid
ARG uid
ARG deno_version

RUN groupadd -g ${gid} deno && \
    useradd -u ${uid} -g ${gid} -s /bin/bash -m deno

RUN apt update && \
    apt install -y \
        curl git unzip vim \
        && \
    apt clean && rm -rf /var/lib/apt/lists/*

USER deno

ENV HOME="/home/deno"
ENV DENO_DIR="$HOME/.deno/cache"
ENV DENO_INSTALL="$HOME/.deno/build"
ENV PATH="$DENO_INSTALL/bin:$PATH"

RUN curl -fsSL https://deno.land/install.sh | sh -s ${deno_version}
