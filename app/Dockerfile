FROM python:3.10-alpine

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

WORKDIR /usr/src/app

RUN apt-get update \
  && apt-get -y install gcc postgresql \
  && apt-get clean

RUN pip install pipenv
COPY Pipfile Pipfile.lock ./
RUN pipenv install --system

COPY . .

RUN python manage.py collectstatic --no-input
