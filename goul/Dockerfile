# vim: set ts=4 sw=4 expandtab:
FROM scinix/golang

RUN apk add --no-cache gcc musl-dev libpcap-dev ;\
    go get github.com/hyeoncheon/goul/cmd/goul ;\
    bin/goul --version ;\
    true

CMD /go/bin/goul -DT -s
