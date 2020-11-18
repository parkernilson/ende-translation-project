# ENDE Translation Project
This container-based project is a website which performs translation from English to German using one of [OpenNMT's pretrained translation models](https://opennmt.net/Models-tf/).

## Requirements
This project requires Docker and Docker Compose to run.

## Clone this repo
To clone this repo, use the command:
```
$ git clone https://github.com/parkernilson/ende-translation-project.git --recursive
```
The `--recursive` flag is required in order to fetch the submodules.

## To run
To run this project, use the docker-compose.yml configurations. There is one for development and one for production.

To run development:
```
$ docker-compose -f docker-compose.dev.yml up --build
```
To run "production" on local computer (run the same images as would run on production, but on local computer):
```
$ docker-compose up --build
```
To run on the production server:
```
$ docker-compose up
```
and whenever changes are made to the remote images, the following command should be run to update them on the server:
```
$ docker-compose pull
```

The client will be accessible at `localhost:5001`.

The server will be accessible at `localhost:5000`.