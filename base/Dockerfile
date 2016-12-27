FROM babim/alpinebase

# environment
ENV JAVA_VERSION=8 \
    JAVA_UPDATE=111 \
    JAVA_BUILD=14 \
    JAVA_PACKAGE=jdk \
    JAVA_HOME=/jre

ENV GLIBC_PKG_VERSION=2.23-r3 \
    GOSU_VERSION=1.9

# install download tool
RUN apk add --no-cache wget curl ca-certificates

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

# install gosu
RUN curl -o /usr/local/bin/gosu -sSL "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-amd64" && \
    chmod +x /usr/local/bin/gosu
