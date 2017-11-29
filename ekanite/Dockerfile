FROM golang:alpine
RUN apk --no-cache add git
ENV CGO_ENABLED=0
RUN go get -v github.com/ekanite/ekanite/cmd/ekanited

#FROM scratch
FROM alpine
COPY --from=0 /go/bin/ekanited /
CMD ["/ekanited", "-tcp", ":5514", "-query", ":9950", "-queryhttp", ":8080", "-diag", ":9951", "-udp", ":5514"]

