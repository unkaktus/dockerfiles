# Generate gogoproto gRPC stub, grpc-gateway stub
# and swagger description from protofiles.
# docker run --rm -ti -v /some/include:/proto-include-custom:ro -v $PWD:/root protoapi-gen *.proto

FROM golang:alpine
RUN apk add --no-cache ca-certificates git

RUN go get -v github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway
RUN go get -v github.com/grpc-ecosystem/grpc-gateway/protoc-gen-swagger
RUN go get -v github.com/gogo/protobuf/protoc-gen-gofast


FROM alpine
RUN apk add --no-cache protobuf

RUN mkdir -p /go/bin
COPY --from=0 /go/bin/ /go/bin
ENV PATH="${PATH}:/go/bin"

RUN mkdir /proto-include-custom
RUN mkdir /proto-include
COPY --from=0 /go/src/github.com/grpc-ecosystem/grpc-gateway/third_party/googleapis/ /proto-include
COPY --from=0 /go/src/github.com/gogo/protobuf/protobuf/ /proto-include

WORKDIR /root
ENTRYPOINT ["protoc", "-I/proto-include", "-I/proto-include-custom", "-I.", "--gofast_out=plugins=grpc:.", "--grpc-gateway_out=logtostderr=true:.", "--swagger_out=logtostderr=true:."]
