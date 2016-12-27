FROM babim/elasticsearch:base

ENV ES_VERSION 2.0.2

WORKDIR /tmp

# Install Elasticsearch
RUN curl -Ls http://download.elasticsearch.org/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/$ES_VERSION/elasticsearch-$ES_VERSION.tar.gz | tar -xz -C /usr/share && \
    mv /usr/share/elasticsearch-$ES_VERSION /usr/share/elasticsearch
COPY ./elasticsearch.yml /usr/share/elasticsearch/elasticsearch.yml
COPY logging.yml /usr/share/elasticsearch/config/
COPY docker-entrypoint.sh /

# clean temp and remove unneed apps
RUN apk del curl wget ca-certificates && \
    rm -fr /tmp/* /var/cache/apk/*

ENV PATH /usr/share/elasticsearch/bin:$PATH

# Add elasticsearch user+group:
RUN addgroup -S elasticsearch && \
    adduser -S -G elasticsearch elasticsearch

RUN set -ex \
    && for path in \
       /usr/share/elasticsearch/data \
       /usr/share/elasticsearch/logs \
       /usr/share/elasticsearch/config \
       /usr/share/elasticsearch/config/scripts \
       ; do \
         mkdir -p "$path"; \
         chown -R elasticsearch:elasticsearch "$path"; \
       done

RUN /usr/share/elasticsearch/bin/plugin install mobz/elasticsearch-head && \
    /usr/share/elasticsearch/bin/plugin install lmenezes/elasticsearch-kopf/2.0

VOLUME ["/usr/share/elasticsearch/data"]

EXPOSE 9200
EXPOSE 9300

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["elasticsearch", "-Des.network.host=0.0.0.0"]
