# Pull base image.
FROM java:8-jdk

ENV ES_VERSION=1.4.0
ENV ES_DIR=/usr/share

#ADD https://download.elasticsearch.org/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/$ES_VERSION/elasticsearch-$ES_VERSION.tar.gz /tmp/es.tgz
COPY ./elasticsearch-1.4.0.tar.gz  /tmp/es.tgz

RUN cd $ES_DIR && \  
  tar xvf /tmp/es.tgz   && \
  rm /tmp/es.tgz

RUN mv $ES_DIR/elasticsearch-$ES_VERSION $ES_DIR/elasticsearch

ENV ES_HOME=$ES_DIR/elasticsearch \
    OPTS=-Dnetwork.host=_non_loopback_ \
    DEFAULT_ES_USER=elsearch

RUN $ES_HOME/bin/plugin install mobz/elasticsearch-head

WORKDIR $ES_HOME

RUN groupadd elsearch
RUN useradd elsearch -g elsearch -p elasticsearch
RUN chown -R elsearch:elsearch  $ES_HOME

RUN echo "cluster.name: TwitterDB" >> $ES_HOME/config/elasticsearch.yml
RUN echo "network.host: 0.0.0.0" >> $ES_HOME/config/elasticsearch.yml

EXPOSE 9200 9300
 

ENTRYPOINT ["/usr/share/elasticsearch/bin/elasticsearch" ] 



