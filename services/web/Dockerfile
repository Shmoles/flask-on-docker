FROM python:3.11-slim-bookworm

# prevent python from writing pyc files and force stdout/stderr to be unbuffered
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /usr/src/app

# system deps (netcat used by the entrypoint/wait scripts)
RUN apt-get update \
  && apt-get install -y --no-install-recommends netcat-openbsd \
  && rm -rf /var/lib/apt/lists/*

# install python deps
COPY ./requirements.txt /usr/src/app/requirements.txt
RUN pip install --upgrade pip \
  && pip install -r requirements.txt

# copy project
COPY . /usr/src/app/

