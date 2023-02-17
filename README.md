# Docker files


This repo has the Docker files for various projects.

## How to build

```
your_dockerhub_name=berndpfrommer
image_name=foo
docker build -t ${your_dockerhub_name}/${image_name} - < Dockerfile.${image_name}
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
