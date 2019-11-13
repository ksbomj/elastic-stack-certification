FROM alpine:3.10

MAINTAINER Andrii Tarykin <ksbomj@gmail.com>

ENV KIBANA_VERSION 7.4.2

RUN apk add shadow bash --no-cache && useradd -m kibana

RUN wget "https://artifacts.elastic.co/downloads/kibana/kibana-$KIBANA_VERSION-linux-x86_64.tar.gz" -O kibana.tar.gz
RUN tar -xzf kibana.tar.gz && rm kibana.tar.gz && mv "kibana-$KIBANA_VERSION" /home/elastic/kibana