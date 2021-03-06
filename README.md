# OctoPrint-docker [![Build Status](https://travis-ci.org/OctoPrint/docker.svg?branch=master)](https://travis-ci.org/OctoPrint/docker)

This repository contains everything you need to run [Octoprint](https://github.com/foosel/OctoPrint) in a docker environment.

I have also built a python2 version, because not all plugins have been ported to python3 yet. So far there is no reason why not, I would still prefer python3.

I noticed that I forgot one "dot" in the tags, it will be fixed next week.

the python3 version is available for all three major architectures (amd64, arm64, arm)
the python2 will follow soon

# Getting started

```
git clone https://github.com/OctoPrint/docker.git octoprint-docker && cd octoprint-docker

# search for you 3D printer serial port (usually it's /dev/ttyUSB0 or /dev/ttyACM0)
ls /dev | grep tty

// edit the docker-compose file to set your 3D printer serial port
vi docker-compose.yml

docker-compose up -d
```

You can then go to http://localhost:5000

You can display the log using `docker-compose logs -f`

## Without docker-compose
```
docker run -d -v ./config:/home/octoprint/.octoprint --device /dev/ttyACM0:/dev/ttyACM0 -p 5000:5000 --name octoprint octoprint/octoprint

```

# Additional tools

## mjpg-streamer (webcam access)

the matching mjpg-streamer container I have linked here with instruction:

https://hub.docker.com/r/badsmoke/mjpg-streamer


## FFMPEG

Octoprint allows you to make timelapses using an IP webcam and ffmpeg. It is installed in `/opt/ffmpeg/ffmpeg`

## Cura Engine

Octoprint allows you to import .STL files and slice them directly in the application. For this you need to upload the profiles that you want to use (you can export them from Cura). Cura Engine is installed in `/opt/cura/CuraEngine`.
