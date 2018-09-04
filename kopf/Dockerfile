FROM babim/alpinebase

ENV ES_VERSION 2.4.4
ENV ES 2
ENV DOWNLOAD_URL "https://download.elastic.co/elasticsearch/release/org/elasticsearch/distribution"
ENV ES_TARBAL "${DOWNLOAD_URL}/tar/elasticsearch/${ES_VERSION}/elasticsearch-${ES_VERSION}.tar.gz"

# install
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/elasticsearch_install.sh | bash
# remove packages
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/elasticsearch_clean.sh | bash

ENV PATH /usr/share/elasticsearch/bin:$PATH
ENV ES_TMPDIR /usr/share/elasticsearch/tmp

WORKDIR /usr/share/elasticsearch

# Install kopf plugin
RUN plugin install lmenezes/elasticsearch-kopf/v2.1.2

ENTRYPOINT ["/docker-entrypoint.sh"]
VOLUME ["/usr/share/elasticsearch/data"]

EXPOSE 9200 9300

CMD ["elasticsearch"]