FROM babim/alpinebase

# CODE BASE #

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

# CODE 6.3 #

ENV ES_VERSION 6.3.0

ENV DOWNLOAD_URL "https://artifacts.elastic.co/downloads/elasticsearch"
ENV ES_TARBAL "${DOWNLOAD_URL}/elasticsearch-${ES_VERSION}.tar.gz"

RUN cd /tmp \
  && echo "===> Install Elasticsearch..." \
  && wget --no-check-certificate --progress=bar:force -O elasticsearch.tar.gz "$ES_TARBAL"; \
  tar -xf elasticsearch.tar.gz \
  && ls -lah \
  && mv elasticsearch-$ES_VERSION /usr/share/elasticsearch \
  && echo "===> Creating Elasticsearch Paths..." \
  && for path in \
  	/usr/share/elasticsearch/data \
  	/usr/share/elasticsearch/logs \
  	/usr/share/elasticsearch/config \
  	/usr/share/elasticsearch/config/scripts \
	/usr/share/elasticsearch/tmp \
  	/usr/share/elasticsearch/plugins \
  ; do \
  mkdir -p "$path"; \
  chown -R elasticsearch:elasticsearch "$path"; \
  done \
  && rm -rf /tmp/* \
  && apk del --purge wget ca-certificates gnupg openssl

WORKDIR /usr/share/elasticsearch
ENV PATH /usr/share/elasticsearch/bin:$PATH
ENV ES_TMPDIR /usr/share/elasticsearch/tmp

# Install X-Pack plugin
# RUN elasticsearch-plugin install -b x-pack
# Install geoip/user-agent plugin
RUN elasticsearch-plugin install -b ingest-geoip
RUN elasticsearch-plugin install -b ingest-user-agent

COPY config/elastic /usr/share/elasticsearch/config
COPY config/x-pack/log4j2.properties /usr/share/elasticsearch/config/x-pack/
COPY config/logrotate /etc/logrotate.d/elasticsearch

ENTRYPOINT ["/docker-entrypoint.sh"]
VOLUME ["/usr/share/elasticsearch/data"]

EXPOSE 9200 9300

CMD ["elasticsearch"]
