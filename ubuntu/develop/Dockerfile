FROM ubuntu:24.04
WORKDIR /opt/StaticJinjaPlus/
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3.12-venv \
    && rm -rf /var/lib/apt/lists/*
ADD https://github.com/MrDave/StaticJinjaPlus.git .
RUN python3 -m venv venv && venv/bin/pip3 install --no-cache-dir -r requirements.txt
ENTRYPOINT ["venv/bin/python3", "main.py"]
CMD ["--srcpath=./templates", "--outpath=./build"]