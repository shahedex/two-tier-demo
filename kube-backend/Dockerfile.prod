FROM python:3.8.7-slim-buster

RUN mkdir /app
WORKDIR /app

RUN apt-get update -y 
RUN apt-get install -y python-pip python-dev

COPY ./requirements.txt /app/requirements.txt

RUN pip install -r requirements.txt

ADD . /app

EXPOSE 5000

CMD flask run --host=0.0.0.0
