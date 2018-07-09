FROM babim/elasticsearch:base

ENV ELASTICSEARCH_VERSION 1.5.2

WORKDIR /usr/share/elasticsearch
ENV PATH /usr/share/elasticsearch/bin:$PATH

# Install Elasticsearch
RUN wget --no-check-certificate --progress=bar:force -O elasticsearch.tar.gz https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-$ELASTICSEARCH_VERSION.tar.gz && \
	tar -xf elasticsearch.tar.gz --strip-components=1; \	
	rm elasticsearch.tar.gz; \
	mkdir -p ./plugins; \
	for path in \
		./data \
		./logs \
		./config \
		./config/scripts \
	; do \
		mkdir -p "$path"; \
		chown -R elasticsearch:elasticsearch "$path"; \
	done; \
	\
	if [ "${ELASTICSEARCH_VERSION%%.*}" -gt 1 ]; then \
		elasticsearch --version; \
	else \
# elasticsearch 1.x doesn't support --version
# but in 5.x, "-v" is verbose (and "-V" is --version)
		elasticsearch -v; \
	fi

COPY config ./config
COPY docker-entrypoint.sh /

# clean temp and remove unneed apps
RUN apk del --purge ca-certificates openssl wget

ENV PATH /usr/share/elasticsearch/bin:$PATH
ENV ES_TMPDIR /usr/share/elasticsearch/tmp