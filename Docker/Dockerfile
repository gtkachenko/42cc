FROM python:3.11-alpine

ARG POETRY_VERSION=1.6.1

RUN apk update && \
    apk add --no-cache curl gcc libressl-dev musl-dev libffi-dev && \
    pip install --no-cache-dir poetry==${POETRY_VERSION} && \
    apk del curl gcc libressl-dev musl-dev libffi-dev

WORKDIR /opt

COPY calc/ /opt/

RUN poetry install

CMD ["poetry", "run", "python", "manage.py", "runserver", "0.0.0.0:8000"]
