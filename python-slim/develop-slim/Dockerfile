FROM python:3.12-slim
WORKDIR /opt/StaticJinjaPlus/
ADD https://github.com/MrDave/StaticJinjaPlus.git .
RUN python3 -m venv venv && venv/bin/pip3 install --no-cache-dir -r requirements.txt
ENTRYPOINT ["venv/bin/python3", "main.py"]
CMD ["--srcpath=./templates", "--outpath=./build"]