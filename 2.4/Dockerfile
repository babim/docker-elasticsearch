FROM alpine:3.5

# download option
RUN apk add --no-cache curl bash && \
	curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20SCRIPT%20AUTO/option.sh -o /option.sh && \
	chmod 755 /option.sh

# copyright and timezone
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20SCRIPT%20AUTO/copyright.sh | bash

ENV ES_VERSION 2.4.4
ENV ES 2
ENV DOWNLOAD_URL "https://download.elastic.co/elasticsearch/release/org/elasticsearch/distribution"
ENV ES_TARBAL "${DOWNLOAD_URL}/tar/elasticsearch/${ES_VERSION}/elasticsearch-${ES_VERSION}.tar.gz"
ENV SOFT elasticsearch

# install
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/${SOFT}_install.sh | bash

ENV PATH /usr/share/elasticsearch/bin:$PATH
ENV ES_TMPDIR /usr/share/elasticsearch/tmp

WORKDIR /usr/share/elasticsearch
VOLUME ["/usr/share/elasticsearch/data"]
EXPOSE 9200 9300

ENTRYPOINT ["/start.sh"]
CMD ["elasticsearch"]
#CMD ["/sbin/tini","--","/usr/bin/supervisord","-c", "/etc/supervisor/supervisord.conf"]