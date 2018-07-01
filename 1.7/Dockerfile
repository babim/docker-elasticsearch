FROM babim/elasticsearch:base

ENV ES_VERSION 1.7.6

ENV DOWNLOAD_URL "https://download.elastic.co/elasticsearch/elasticsearch"
ENV ES_TARBAL "${DOWNLOAD_URL}/elasticsearch-${ES_VERSION}.tar.gz"

RUN cd /tmp \
  && echo "===> Install Elasticsearch..." \
  && wget --no-check-certificate -O elasticsearch.tar.gz "$ES_TARBAL"; \
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
  && apk del .build-deps  wget

COPY config/elastic /usr/share/elasticsearch/config
COPY config/logrotate /etc/logrotate.d/elasticsearch

WORKDIR /usr/share/elasticsearch