FROM ubuntu:20.04

USER root
RUN --mount=type=cache,id=apt,target=/var/cache/apt \
    apt update && apt install -y git sextractor python3-pip ca-certificates python3-urllib3 vim\
    && rm -rf /var/lib/apt/lists/*

RUN --mount=type=cache,id=apt,target=/var/cache/apt \
    mkdir project \
    && mkdir project/config

RUN --mount=type=cache,id=pip,uid=9000,gid=9000,target=/home/ana/ \
    pip install --index-url https://pypi.tuna.tsinghua.edu.cn/simple/ numpy astropy

COPY . project/

WORKDIR /project/config

RUN --mount=type=cache,id=apt,target=/var/cache/apt \
    source-extractor -d > default.sex \
    && source-extractor -dp > default.param

WORKDIR /project