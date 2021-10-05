# Golang Cross

This repository holds my custom docker image of golang build container.

It based on the alpine-glibc image by Vlad Frolov (frolvlad/alpine-glibc) for pre-compiled version of official golang distribution. With this image, you can build musl libc linked executables with glibc version of golang compiler.



## Build, Tag, and Push

Now hub.docker.com does not provide automatic image build via push webhook for free accounts. Sad news.

### Build

Build locally...

```
sio4@entry:~/git/sio4/docker-library/golang$ sudo docker build -t golang:1.16.7 .
Sending build context to Docker daemon  3.584kB
Step 1/9 : FROM frolvlad/alpine-glibc:alpine-3.12_glibc-2.31
alpine-3.12_glibc-2.31: Pulling from frolvlad/alpine-glibc
e519532ddf75: Pull complete 
0fad380f35a4: Pull complete 
Digest: sha256:8c34decaa817b9ed560b020129c653f3e0845953543efebb3b07a13b4b7d640e
Status: Downloaded newer image for frolvlad/alpine-glibc:alpine-3.12_glibc-2.31
 ---> f43a9f66ec5c
Step 2/9 : ENV BASE_VER alpine-3.12_glibc-2.31
 ---> Running in 65aa2a68d42d
Removing intermediate container 65aa2a68d42d
 ---> de93505ef929
Step 3/9 : ENV GO_VER 1.16.7
 ---> Running in 26fba8311114
Removing intermediate container 26fba8311114
 ---> c74222c1d89d
Step 4/9 : ENV GO_OS linux
 ---> Running in 365083c79b4a
Removing intermediate container 365083c79b4a
 ---> debc0cd3eff7
Step 5/9 : ENV GO_ARCH amd64
 ---> Running in 0f7a57877adf
Removing intermediate container 0f7a57877adf
 ---> a0047ea0798f
Step 6/9 : ENV PATH $GOPATH/bin:/opt/go/bin:$PATH
 ---> Running in 4847e2c082c1
Removing intermediate container 4847e2c082c1
 ---> 5ff465bf4bfe
Step 7/9 : ENV GOPATH /go
 ---> Running in 4a3e41ae8206
Removing intermediate container 4a3e41ae8206
 ---> 5e2278819168
Step 8/9 : RUN mkdir -p $GOPATH/src $GOPATH/bin ;     apk add --no-cache ca-certificates ;     apk add --no-cache git ;     mkdir -p /opt ;     wget -q -O - https://golang.org/dl/go$GO_VER.$GO_OS-$GO_ARCH.tar.gz 	| tar -C /opt/ -zxf -
 ---> Running in 49111be79b8f
fetch http://dl-cdn.alpinelinux.org/alpine/v3.12/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.12/community/x86_64/APKINDEX.tar.gz
(1/1) Installing ca-certificates (20191127-r4)
Executing busybox-1.31.1-r20.trigger
Executing ca-certificates-20191127-r4.trigger
OK: 18 MiB in 18 packages
fetch http://dl-cdn.alpinelinux.org/alpine/v3.12/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.12/community/x86_64/APKINDEX.tar.gz
(1/5) Installing nghttp2-libs (1.41.0-r0)
(2/5) Installing libcurl (7.79.1-r0)
(3/5) Installing expat (2.2.9-r1)
(4/5) Installing pcre2 (10.35-r0)
(5/5) Installing git (2.26.3-r0)
Executing busybox-1.31.1-r20.trigger
Executing glibc-bin-2.31-r0.trigger
/usr/glibc-compat/sbin/ldconfig: /usr/glibc-compat/lib/ld-linux-x86-64.so.2 is not a symbolic link

OK: 33 MiB in 23 packages
Removing intermediate container 49111be79b8f
 ---> 59552eb2c293
Step 9/9 : WORKDIR $GOPATH
 ---> Running in 647d6f0a9371
Removing intermediate container 647d6f0a9371
 ---> f11b0cb311e8
Successfully built f11b0cb311e8
Successfully tagged golang:1.16.7
sio4@entry:~/git/sio4/docker-library/golang$
```

### Push the image with tags

Tagging and pushing the image.

```
sio4@entry:~/git/sio4/docker-library/golang$ sudo docker image tag golang:1.16.7 scinix/golang:1.16.7
sio4@entry:~/git/sio4/docker-library/golang$ sudo docker image tag golang:1.16.7 scinix/golang:latest
sio4@entry:~/git/sio4/docker-library/golang$ sudo docker push scinix/golang:1.16.7
The push refers to repository [docker.io/scinix/golang]
b0a120dc57c0: Preparing 
7d97f077ffbf: Preparing 
e6688e911f15: Preparing 
denied: requested access to the resource is denied
sio4@entry:~/git/sio4/docker-library/golang$ sudo docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: scinix
Password: 
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
sio4@entry:~/git/sio4/docker-library/golang$ sudo docker push scinix/golang:1.16.7
The push refers to repository [docker.io/scinix/golang]
b0a120dc57c0: Pushed 
7d97f077ffbf: Mounted from frolvlad/alpine-glibc 
e6688e911f15: Mounted from frolvlad/alpine-glibc 
1.16.7: digest: sha256:f4d2be757f87efd66ec989c53cff400f21ff50a51c85a8e714e1d3940983cab9 size: 952
sio4@entry:~/git/sio4/docker-library/golang$ sudo docker push scinix/golang:latest
The push refers to repository [docker.io/scinix/golang]
b0a120dc57c0: Layer already exists 
7d97f077ffbf: Layer already exists 
e6688e911f15: Layer already exists 
latest: digest: sha256:f4d2be757f87efd66ec989c53cff400f21ff50a51c85a8e714e1d3940983cab9 size: 952
sio4@entry:~/git/sio4/docker-library/golang$ 
```


