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
$ docker-compose pull && docker-compose up
```
and whenever changes are made to the remote images, the following command should be run to update them on the server:
```
$ docker-compose pull
```

In development, the client will be accessible at `localhost:5001` and the server will be accessible at `localhost:5000`.

In production, the application will be served behind an NGINX reverse proxy.

## Note about including pretrained model
The translation server service will look for the pretrained model in `~/ml_models` for the pretrained model. This means that if you run `docker-compose up` as `root` it will look in `/home` and if you run it as a non-root user, it will look in `/home/${USER}`.

## Hosting
As of 11/19/2020, this project is hosted on a digital ocean Docker droplet.

### Deployment
For simplicity, this github project is cloned on the droplet, and it is deployed by pulling from this repository, then building the containers on the server manually. The containers are orchestrated with Docker Compose.