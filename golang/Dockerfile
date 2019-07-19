# vim: set ts=4 sw=4 expandtab:
FROM frolvlad/alpine-glibc:alpine-3.7_glibc-2.26

ENV GO_VER 1.9.4
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
