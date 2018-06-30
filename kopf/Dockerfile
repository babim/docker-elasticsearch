FROM babim/elasticsearch:2.4

WORKDIR /usr/share/elasticsearch

COPY config/elastic /usr/share/elasticsearch/config
COPY config/logrotate /etc/logrotate.d/elasticsearch

# Install kopf plugin
RUN plugin install lmenezes/elasticsearch-kopf/v2.1.2
