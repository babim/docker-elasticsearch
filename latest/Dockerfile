FROM babim/elasticsearch:base

ENV ES_VERSION 6.3.1
ENV ES 6
ENV DOWNLOAD_URL "https://artifacts.elastic.co/downloads/elasticsearch"
ENV ES_TARBAL "${DOWNLOAD_URL}/elasticsearch-${ES_VERSION}.tar.gz"

# install
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/elasticsearch_install.sh | bash
# remove packages
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/elasticsearch_clean.sh | bash

ENV PATH /usr/share/elasticsearch/bin:$PATH
ENV ES_TMPDIR /usr/share/elasticsearch/tmp

WORKDIR /usr/share/elasticsearch

ENTRYPOINT ["/start.sh"]
VOLUME ["/usr/share/elasticsearch/data"]

EXPOSE 9200 9300

CMD ["elasticsearch"]