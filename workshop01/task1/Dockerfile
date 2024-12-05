FROM python:3.10.15-bullseye

LABEL APP_NAME="PYTHON BEAR"

ARG APP_DIR=/app

WORKDIR ${APP_DIR}

ENV PORT=3000 \
    INSTANCE_NAME="" \
    INSTANCE_HASH=""

COPY public public
COPY templates templates
COPY main.py requirements.txt run.sh utils.py ./

RUN pip install -r requirements.txt

EXPOSE ${PORT}

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${PORT}/healthz > /dev/null || exit 1

# Run with shell
ENTRYPOINT ["python", "main.py"]
CMD []

# Terminal command to build container
# docker container run -d -e PORT=5000 -e INSTANCE_NAME=NAME -e INSTANCE_HASH=HASH -p 5000:5000 --name dov-bear movingcastle888/dov-bear:v0.0.1 