FROM alpine:3.20

ENV SPRING_OUTPUT_ANSI_ENABLED=ALWAYS \
    JHIPSTER_SLEEP=0 \
    JAVA_OPTS=""

# Install OpenJDK 11 (multi-arch: works on ARM64 & AMD64)
RUN apk add --no-cache openjdk11 curl

RUN adduser -D -s /bin/sh jhipster
WORKDIR /home/jhipster

COPY build/libs/tripmgmt-0.0.1-SNAPSHOT.jar app.jar
COPY entrypoint.sh /home/jhipster/
RUN chmod 755 /home/jhipster/entrypoint.sh && chown jhipster:jhipster /home/jhipster/entrypoint.sh
RUN java -version && uname -m

USER jhipster

ENTRYPOINT ["java", "-jar", "/home/jhipster/app.jar"]

EXPOSE 8080