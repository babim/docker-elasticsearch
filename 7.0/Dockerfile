FROM babim/elasticsearch:base

ENV ES_VERSION 7.0.0
ENV ES 7
ENV BIT x86_64
ENV DOWNLOAD_URL "https://artifacts.elastic.co/downloads/elasticsearch"
ENV ES_TARBAL "${DOWNLOAD_URL}/elasticsearch-oss-${ES_VERSION}-linux-${BIT}.tar.gz"
ENV SOFT elasticsearch

# install
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/${SOFT}_install.sh | bash

ENV PATH /usr/share/elasticsearch/bin:$PATH
ENV ES_TMPDIR /usr/share/elasticsearch/tmp

WORKDIR /usr/share/elasticsearch
VOLUME ["/usr/share/elasticsearch/data"]
EXPOSE 9200 9300
