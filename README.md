# Docker files


This repo has the Docker files for various projects.

## How to build

```
your_dockerhub_name=berndpfrommer
image_name=foo
docker build . -t ${your_dockerhub_name}/${image_name} -f  Dockerfile.${image_name}
```

## List your images
```
docker image list
```

## How to upload to dockerhub:
```
docker login
docker push ${your_dockerhub_name}/${image_name}
```


## How to test
```
docker run -it ${your_dockerhub_name}/${image_name}:latest /bin/bash
```

## How to run interactively as user pfrommer with X11 forwarding

```
docker run -v /home/pfrommer:/home/pfrommer -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -w /home/pfrommer -u $(id -u ${USER}):$(id -g ${USER}) -it berndpfrommer/focal_noetic_dev /bin/bash
```

## How to connect as root to a running container

```bash
docker exec -u root -it <container-id> /bin/bash
```