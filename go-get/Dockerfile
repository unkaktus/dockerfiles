# go-get-ing Go binaries
# docker run --rm -ti -v $HOME/go/bin:/go/bin:rw go-get -v github.com/nogoegst/redir
FROM golang:alpine

RUN apk add --no-cache git mercurial

ENV CGO_ENABLED=0
ENTRYPOINT ["go", "get"]
