FROM golang:alpine
RUN apk --no-cache add git protobuf-dev
RUN go get -u -v github.com/golang/protobuf/protoc-gen-go

RUN go get -v github.com/rapidloop/nrpc
WORKDIR /go/src/github.com/rapidloop/nrpc
RUN go get -v ./...

RUN go install ./protoc-gen-nrpc
RUN go generate ./examples/...
