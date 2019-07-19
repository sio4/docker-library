# vim: set ts=4 sw=4 expandtab:
#
# https://hub.docker.com/r/scinix/golang
# https://hub.docker.com/r/frolvlad/alpine-glibc

FROM frolvlad/alpine-glibc:alpine-3.9_glibc-2.28

ENV GO_VER 1.12.7
ENV GO_OS linux
ENV GO_ARCH amd64

ENV PATH $GOPATH/bin:/opt/go/bin:$PATH
ENV GOPATH /go

RUN mkdir -p $GOPATH/src $GOPATH/bin ; \
    apk add --no-cache ca-certificates ; \
    apk add --no-cache git ; \
    mkdir -p /opt ; \
    wget -q -O - https://dl.google.com/go/go$GO_VER.$GO_OS-$GO_ARCH.tar.gz \
	| tar -C /opt/ -zxf -

WORKDIR $GOPATH
