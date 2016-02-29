FROM andreptb/oracle-java:8

ONBUILD COPY $FILE $FILE
ONBUILD EXPOSE 8080
ONBUILD ENTRYPOINT ["/bin/sh","-c","java -Djava.security.egd=file:/dev/./urandom $JAVA_OPTS -jar $FILE"]
