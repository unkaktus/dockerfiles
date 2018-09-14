FROM ubuntu:17.10
RUN apt-get update
RUN apt-get install -y git make clang libasound2-dev

RUN git clone https://github.com/ratchov/sndio
WORKDIR sndio
RUN ./configure
RUN make

RUN mkdir -p /sndio-bin
RUN make install

RUN apt-get install -y libpulse-dev pulseaudio libltdl-dev

WORKDIR /
RUN git clone https://github.com/t6/pulseaudio-module-sndio
WORKDIR /pulseaudio-module-sndio
RUN make
