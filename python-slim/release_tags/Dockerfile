FROM python:3.12-slim
WORKDIR /opt/StaticJinjaPlus/
ARG HASH
ARG TAG
ADD --checksum=sha256:$HASH https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/$TAG.tar.gz /tmp/app.tar.gz
RUN tar xzf /tmp/app.tar.gz --strip-components=1 -C . && rm /tmp/app.tar.gz
RUN python3 -m venv venv && venv/bin/pip3 install --no-cache-dir -r requirements.txt
ENTRYPOINT ["venv/bin/python3", "main.py"]
CMD ["--srcpath=./templates", "--outpath=./build"]