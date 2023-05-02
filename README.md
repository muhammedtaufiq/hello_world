# hello_world
assignment 3.5

**Most importantly make sure Repo is created in Git
Start from here-->
https://docs.docker.com/compose/gettingstarted/
#
then create the app.py using steps above in Visual Studio in hello world folder.
git clone repo
git add *
git commit -m "first commit"
git push

check in repo.

then in VS hello world folder continue below

  1.Created #requirements.txt ( flask, redis) in line 1 & 2
  2.created #dockerfile with content below:

syntax=docker/dockerfile:1
FROM python:3.7-alpine
WORKDIR /code
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
EXPOSE 5000
COPY . .
CMD ["flask", "run"]

  3.Created #docker-compose.yml,with content below:

version: "3.9"
services:
  web:
    build: .
    ports:
      - "8000:5000"
  redis:
    image: "redis:alpine"
    
   4. Run docker DESKTOP
   5. VS Studio terminal "docker compose up"
   6. container will be running
