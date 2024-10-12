FROM ubuntu:24.04
WORKDIR /opt/StaticJinjaPlus/
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3.12-venv \
    && rm -rf /var/lib/apt/lists/*
ARG HASH
ARG TAG
ADD --checksum=sha256:$HASH https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/$TAG.tar.gz /tmp/app.tar.gz
RUN tar xzf /tmp/app.tar.gz --strip-components=1 -C . && rm /tmp/app.tar.gz
RUN python3 -m venv venv && venv/bin/pip3 install --no-cache-dir -r requirements.txt
ENTRYPOINT ["venv/bin/python3", "main.py"]
CMD ["--srcpath=./templates", "--outpath=./build"]