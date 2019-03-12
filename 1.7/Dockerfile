FROM alpine:3.4

## alpine linux
RUN apk add --no-cache wget bash && cd / && wget --no-check-certificate https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20SCRIPT%20AUTO/option.sh && \
    chmod 755 /option.sh

# copyright and timezone
RUN wget --no-check-certificate -O - https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20SCRIPT%20AUTO/copyright.sh | bash

ENV ES_VERSION 1.7.6
ENV ES 1
ENV DOWNLOAD_URL "https://download.elastic.co/elasticsearch/elasticsearch"
ENV ES_TARBAL "${DOWNLOAD_URL}/elasticsearch-${ES_VERSION}.tar.gz"

# install
RUN wget --no-check-certificate -O - https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/elasticsearch_install.sh | bash

ENV PATH /usr/share/elasticsearch/bin:$PATH
ENV ES_TMPDIR /usr/share/elasticsearch/tmp

WORKDIR /usr/share/elasticsearch
VOLUME ["/usr/share/elasticsearch/data"]
EXPOSE 9200 9300

ENTRYPOINT ["/start.sh"]
CMD ["elasticsearch"]
#CMD ["/sbin/tini","--","/usr/bin/supervisord","-c", "/etc/supervisor/supervisord.conf"]