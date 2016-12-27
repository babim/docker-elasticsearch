FROM babim/alpinebase

# environment
ENV JAVA_VERSION=8 \
    JAVA_UPDATE=111 \
    JAVA_BUILD=14 \
    JAVA_PACKAGE=jdk \
    JAVA_HOME=/jre

ENV ES_VERSION 1.7.6
ENV GLIBC_PKG_VERSION=2.23-r3 \
    GOSU_VERSION=1.9

# install download tool
RUN apk add --update wget curl ca-certificates

WORKDIR /tmp

# Install glibc
RUN mkdir -p /etc/apk/keys/ && \
    apk --no-cache add ca-certificates && \
    wget -q --no-check-certificate -O /etc/apk/keys/andyshinn.rsa.pub https://raw.githubusercontent.com/andyshinn/alpine-pkg-glibc/master/andyshinn.rsa.pub && \
    wget -q --no-check-certificate https://github.com/andyshinn/alpine-pkg-glibc/releases/download/$GLIBC_PKG_VERSION/glibc-$GLIBC_PKG_VERSION.apk && \
    apk add glibc-$GLIBC_PKG_VERSION.apk

# Install Oracle Java
RUN curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/$JAVA_VERSIONu$JAVA_UPDATE-b$JAVA_BUILD/server-jre-$JAVA_VERSIONu$JAVA_UPDATE-linux-x64.tar.gz" -o /tmp/java.tar.gz && \
    tar -zxf /tmp/java.tar.gz && \
    mv /tmp/jdk1.${JAVA_VERSION}.0_${JAVA_UPDATE}/jre /jre && \
    rm /jre/bin/jjs && \
    rm /jre/bin/keytool && \
    rm /jre/bin/orbd && \
    rm /jre/bin/pack200 && \
    rm /jre/bin/policytool && \
    rm /jre/bin/rmid && \
    rm /jre/bin/rmiregistry && \
    rm /jre/bin/servertool && \
    rm /jre/bin/tnameserv && \
    rm /jre/bin/unpack200 && \
    rm /jre/lib/ext/nashorn.jar && \
    rm /jre/lib/jfr.jar && \
    rm -rf /jre/lib/jfr && \
    rm -rf /jre/lib/oblique-fonts && \
    echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf

RUN curl -o /usr/local/bin/gosu -sSL "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-amd64" && \
	chmod +x /usr/local/bin/gosu

# Install Elasticsearch
RUN curl -Ls https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-$ES_VERSION.tar.gz | tar -xz -C /usr/share && \
    mv /usr/share/elasticsearch-$ES_VERSION /usr/share/elasticsearch
COPY ./elasticsearch.yml /usr/share/elasticsearch/elasticsearch.yml
COPY docker-entrypoint.sh /

# clean temp and remove unneed apps
RUN apk del curl wget ca-certificates && \
    rm -fr /tmp/* /var/cache/apk/*

ENV PATH /usr/share/elasticsearch/bin:$PATH

# Add elasticsearch user+group:
RUN addgroup -S elasticsearch && \
    adduser -S -G elasticsearch elasticsearch

RUN set -ex \
    && for path in \
       /usr/share/elasticsearch/data \
       /usr/share/elasticsearch/logs \
       /usr/share/elasticsearch/config \
       /usr/share/elasticsearch/config/scripts \
       ; do \
         mkdir -p "$path"; \
         chown -R elasticsearch:elasticsearch "$path"; \
       done

RUN /usr/share/elasticsearch/bin/plugin install mobz/elasticsearch-head && \
    /usr/share/elasticsearch/bin/plugin install lmenezes/elasticsearch-kopf/2.0

VOLUME ["/var/lib/elasticsearch/"]

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["elasticsearch", "-Des.network.host=0.0.0.0"]
