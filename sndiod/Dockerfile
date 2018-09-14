FROM sndio
RUN mkdir /var/run/sndiod
RUN useradd -r -g audio -s /sbin/nologin -d /var/run/sndiod sndiod

USER sndiod
ENTRYPOINT ["sndiod"]
