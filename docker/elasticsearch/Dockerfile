FROM alpine:3.10

MAINTAINER Andrii Tarykin <ksbomj@gmail.com>

ENV JAVA_DISTRIBUTION openjdk
ENV JAVA_VERSION 11
ENV ELASTIC_VERSION 7.4.2
ENV JAVA_HOME /usr

RUN apk add "$JAVA_DISTRIBUTION$JAVA_VERSION" shadow bash --update && \
    rm -rf /var/cache/apk/* && ln -s "/usr/lib/jvm/java-1.$JAVA_VERSION-openjdk/bin/javac" /usr/bin/javac

RUN useradd -m elastic

COPY etc /etc/security/limits.conf

RUN wget "https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-$ELASTIC_VERSION-linux-x86_64.tar.gz" -O elastic.tar.gz && \
    tar -xzf elastic.tar.gz && rm elastic.tar.gz && mv "elasticsearch-$ELASTIC_VERSION" /home/elastic/elasticsearch && \
    chown -R elastic:elastic /home/elastic/elasticsearch && rm -rf /home/elastic/elasticsearch/modules/x-pack-ml

USER elastic

WORKDIR /home/elastic

CMD ["/home/elastic/elasticsearch/bin/elasticsearch", "-p", "pid"]

