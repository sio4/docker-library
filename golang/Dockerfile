# vim: set ts=4 sw=4 expandtab:
#
# https://hub.docker.com/r/scinix/golang
# https://hub.docker.com/r/frolvlad/alpine-glibc
#
# previous: alpine-3.9_glibc-2.28
# candidates: alpine-3.13_glibc-2.33 alpine-3.12_glibc-2.31

FROM frolvlad/alpine-glibc:alpine-3.12_glibc-2.31

ENV BASE_VER alpine-3.12_glibc-2.31
ENV GO_VER 1.16.7
ENV GO_OS linux
ENV GO_ARCH amd64

ENV PATH $GOPATH/bin:/opt/go/bin:$PATH
ENV GOPATH /go

RUN mkdir -p $GOPATH/src $GOPATH/bin ; \
    apk add --no-cache ca-certificates ; \
    apk add --no-cache git ; \
    mkdir -p /opt ; \
    wget -q -O - https://golang.org/dl/go$GO_VER.$GO_OS-$GO_ARCH.tar.gz \
	| tar -C /opt/ -zxf -

WORKDIR $GOPATH
