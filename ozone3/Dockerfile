FROM openjdk:8-jre-alpine

ENV SERVER_ZIP=https://media.forgecdn.net/files/2735/217/PO3-3.0.41-SERVER.zip

RUN apk --no-cache add wget openssl unzip
RUN addgroup -g 1234 minecraft
RUN adduser -D -h /data -u 1234 -G minecraft -g "minecraft user" minecraft

RUN mkdir /tmp/minecraft && cd /tmp/minecraft && \
	wget --quiet -c ${SERVER_ZIP} -O ProjectOzone3.zip && \
	unzip -q ProjectOzone3.zip && \
	rm ProjectOzone3.zip && \
	chown -R minecraft /tmp/minecraft

USER minecraft

EXPOSE 25565
EXPOSE 25575

ADD start.sh /start

VOLUME /data
ADD server.properties /tmp/server.properties
WORKDIR /data

CMD /start

ENV MOTD A Minecraft (Project Ozone 3) Server Powered by Docker
ENV LEVEL ozone3
ENV JVM_OPTS -Xmx6500m -Xms2048m
