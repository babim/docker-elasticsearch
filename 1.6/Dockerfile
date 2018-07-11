FROM babim/elasticsearch:base

ENV ES_VERSION 1.6.2

ENV DOWNLOAD_URL "https://download.elastic.co/elasticsearch/elasticsearch"
ENV ES_TARBAL "${DOWNLOAD_URL}/elasticsearch-${ES_VERSION}.tar.gz"

# ensure elasticsearch user exists
RUN adduser -DH -s /sbin/nologin elasticsearch

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
  	/usr/share/elasticsearch/plugins \
  ; do \
  mkdir -p "$path"; \
  chown -R elasticsearch:elasticsearch "$path"; \
  done \
  && rm -rf /tmp/* \
  && apk del --purge wget ca-certificates gnupg openssl

COPY config ./config

# clean temp and remove unneed apps
RUN apk del --purge ca-certificates openssl wget

ENTRYPOINT ["/docker-entrypoint.sh"]
VOLUME ["/usr/share/elasticsearch/data"]

EXPOSE 9200 9300

CMD ["elasticsearch"]