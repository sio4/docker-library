# Dockerfile Library for Go Language

This is a personal Dockerfile library to build docker images based on golang
development environment.

## Steps

The repository was already configured with Docker Hub and all new tags will
trigger image build on Docker Hub. (https://hub.docker.com/repositories)

After release tagged version of images are built, the following steps are
required to tag a special `latest` tag.  For Docker image tags, `latest` is
not special and it is just a tag named as `latest` literally. But general
understanding of `latest` is somewhat special, so we do following steps so
the tag always points out "latest" release.

```console
$ sudo docker login
$ sudo docker pull scinix/golang:1.12.7
1.12.7: Pulling from scinix/golang
bdf0201b3a05: Already exists
e9c5c69630cb: Already exists
51a36f96410e: Already exists
Digest: sha256:2b3877b51725b56e5b7f524bd1bb9732acf670d00bf0af81ebe6b5068e78c164
Status: Downloaded newer image for scinix/golang:1.12.7
docker.io/scinix/golang:1.12.7
$ sudo docker image tag scinix/golang:1.12.7 scinix/golang:latest
$ sudo docker push scinix/golang:latest
The push refers to repository [docker.io/scinix/golang]
f0a26fcadad0: Layer already exists
c066e60ed0a6: Layer already exists
a464c54f93a9: Layer already exists
latest: digest: sha256:2b3877b51725b56e5b7f524bd1bb9732acf670d00bf0af81ebe6b5068e78c164 size: 952
$
```


Happy Docking!
