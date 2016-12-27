# Portefaix Elasticsearch
Thanks portefaix

Alpine Linux is a Linux distribution built around musl libc and BusyBox.
This image is based on the official Alpine Linux.

The following Elasticsearch plugins are installed :

Some [Elasticsearch][] plugins are available:
* [ElasticSearchHead][]: `http://xxx:9200/_plugin/head/`
* [Kopf][]: `http://xxx:9200/_plugin/kopf/`

Ports exported are : `9200` and `9300`
Volumes exported is : `/usr/share/elasticsearch/data`

## Usage

    $ docker run -it -p 9200:9200 -p 9300:9300 babim/elasticsearch:[version]
