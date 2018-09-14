FROM ubuntu:17.10
RUN apt-get update
RUN apt-get install -y git make clang libasound2-dev

RUN git clone https://github.com/ratchov/sndio
WORKDIR sndio
RUN ./configure
RUN make

RUN mkdir -p /sndio-bin
ENV DESTDIR=/sndio-bin
RUN make install

FROM ubuntu:17.10
RUN apt-get update
RUN apt-get install -y libasound2
COPY --from=0 /sndio-bin/ /
RUN ldconfig

#ENTRYPOINT ["cp", "-a", "/sndio-bin/usr/local/"]
