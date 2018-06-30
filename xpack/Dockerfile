FROM babim/elasticsearch:latest

WORKDIR /usr/share/elasticsearch

# Install X-Pack plugin
# RUN elasticsearch-plugin install -b x-pack
# Install geoip/user-agent plugin
RUN elasticsearch-plugin install -b ingest-geoip
RUN elasticsearch-plugin install -b ingest-user-agent

COPY config/elastic /usr/share/elasticsearch/config
COPY config/x-pack/log4j2.properties /usr/share/elasticsearch/config/x-pack/
COPY config/logrotate /etc/logrotate.d/elasticsearch