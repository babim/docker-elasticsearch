FROM babim/alpinebase

## alpine linux
RUN apk add --no-cache wget bash && cd / && wget --no-check-certificate https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20SCRIPT%20AUTO/option.sh && \
    chmod 755 /option.sh

# Install Oracle Java
RUN apk add --no-cache openjdk8-jre tini su-exec libzmq bash libc6-compat

# ensure elasticsearch user exists
RUN adduser -DH -s /sbin/nologin elasticsearch

RUN apk add --no-cache ca-certificates gnupg openssl

COPY docker-entrypoint.sh /
COPY docker-healthcheck /usr/local/bin/

ENTRYPOINT ["/docker-entrypoint.sh"]
VOLUME ["/usr/share/elasticsearch/data"]

EXPOSE 9200 9300

CMD ["elasticsearch"]
