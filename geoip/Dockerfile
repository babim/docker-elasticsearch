FROM babim/elasticsearch:latest

WORKDIR /usr/share/elasticsearch

# Install geoip/user-agent plugin
RUN elasticsearch-plugin install -b ingest-geoip
RUN elasticsearch-plugin install -b ingest-user-agent

COPY config/elastic /usr/share/elasticsearch/config
COPY config/logrotate /etc/logrotate.d/elasticsearch