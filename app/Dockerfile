#Pull image for Linux Alpine with Python 3.8
FROM python:3.8.0-alpine

#Set the working directory inside the Alpine Container
WORKDIR /usr/src/app

#Set environment variables
#don't write .pyc files to disk
ENV PYTHONDONTWRITEBYTECODE 1
#don't buffer stdout
ENV PYTHONUNBUFFERED 1

#Install dependencies for PostgreSQL (Psycopg2)
RUN apk update \
    && apk add postgresql-dev gcc python3-dev musl-dev

#Install dependencies inside container
RUN pip install --upgrade pip
COPY ./requirements.txt /usr/src/app/requirements.txt
RUN pip install -r requirements.txt

#Copy the entry point file
COPY ./entrypoint.sh /usr/src/app/entrypoint.sh

#Copy all project files (Later: set up an auto sync)
COPY . /usr/src/app/

#Run entrypoint
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]
