# Google Cloud SDK
# docker run --rm -ti -v $HOME:/root gcloud version
FROM alpine

RUN apk add --no-cache curl ca-certificates tar
WORKDIR /root
RUN curl -sSL -O https://dl.google.com/dl/cloudsdk/release/google-cloud-sdk.tar.gz
RUN mkdir google-cloud-sdk
RUN tar xzf google-cloud-sdk.tar.gz -C google-cloud-sdk --strip-components 1


FROM alpine
RUN apk add --no-cache python2
RUN mkdir -p /usr/src/google-cloud-sdk
COPY --from=0 /root/google-cloud-sdk /usr/src/google-cloud-sdk
RUN /usr/src/google-cloud-sdk/install.sh --usage-reporting false --path-update true

WORKDIR /root
ENV PATH $PATH:/usr/src/google-cloud-sdk/bin

ENTRYPOINT ["gcloud"]
