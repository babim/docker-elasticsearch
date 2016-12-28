FROM babim/alpinebase

# Install Oracle Java
RUN apk add --no-cache openjdk8-jre

# ensure elasticsearch user exists
RUN addgroup -S elasticsearch && adduser -S -G elasticsearch elasticsearch

# grab su-exec for easy step-down from root
# and bash for "bin/elasticsearch" among others
RUN apk add --no-cache 'su-exec>=0.2' bash

# install other depend
RUN apk add --no-cache --virtual .fetch-deps \
		ca-certificates \
		openssl \
		tar wget

COPY docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
VOLUME ["/var/lib/elasticsearch/data"]
EXPOSE 9200 9300
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["elasticsearch"]
