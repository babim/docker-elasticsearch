[![](https://images.microbadger.com/badges/image/babim/elasticsearch:base.svg)](https://microbadger.com/images/babim/elasticsearch:base "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:base.svg)](https://microbadger.com/images/babim/elasticsearch:base "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/babim/elasticsearch:lastest.svg)](https://microbadger.com/images/babim/elasticsearch:lastest "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:lastest.svg)](https://microbadger.com/images/babim/elasticsearch:lastest "Get your own version badge on microbadger.com")

[![](https://images.microbadger.com/badges/image/babim/elasticsearch:1.5.svg)](https://microbadger.com/images/babim/elasticsearch:1.5 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:1.5.svg)](https://microbadger.com/images/babim/elasticsearch:1.5 "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/babim/elasticsearch:1.6.svg)](https://microbadger.com/images/babim/elasticsearch:1.6 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:1.6.svg)](https://microbadger.com/images/babim/elasticsearch:1.6 "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/babim/elasticsearch:1.7.svg)](https://microbadger.com/images/babim/elasticsearch:1.7 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:1.7.svg)](https://microbadger.com/images/babim/elasticsearch:1.7 "Get your own version badge on microbadger.com")

[![](https://images.microbadger.com/badges/image/babim/elasticsearch:2.0.svg)](https://microbadger.com/images/babim/elasticsearch:2.0 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:2.0.svg)](https://microbadger.com/images/babim/elasticsearch:2.0 "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/babim/elasticsearch:2.1.svg)](https://microbadger.com/images/babim/elasticsearch:2.1 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:2.1.svg)](https://microbadger.com/images/babim/elasticsearch:2.1 "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/babim/elasticsearch:2.2.svg)](https://microbadger.com/images/babim/elasticsearch:2.2 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:2.2.svg)](https://microbadger.com/images/babim/elasticsearch:2.2 "Get your own version badge on microbadger.com")

[![](https://images.microbadger.com/badges/image/babim/elasticsearch:2.3.svg)](https://microbadger.com/images/babim/elasticsearch:2.3 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:2.3.svg)](https://microbadger.com/images/babim/elasticsearch:2.3 "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/babim/elasticsearch:2.4.svg)](https://microbadger.com/images/babim/elasticsearch:2.4 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:2.4.svg)](https://microbadger.com/images/babim/elasticsearch:2.4 "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/babim/elasticsearch:5.0.svg)](https://microbadger.com/images/babim/elasticsearch:5.0 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:5.0.svg)](https://microbadger.com/images/babim/elasticsearch:5.0 "Get your own version badge on microbadger.com")

[![](https://images.microbadger.com/badges/image/babim/elasticsearch:5.1.svg)](https://microbadger.com/images/babim/elasticsearch:5.1 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/babim/elasticsearch:5.1.svg)](https://microbadger.com/images/babim/elasticsearch:5.1 "Get your own version badge on microbadger.com")

# Elasticsearch
Thanks portefaix and official elasticsearch repo

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

Don't use tag :base ok ? :-)