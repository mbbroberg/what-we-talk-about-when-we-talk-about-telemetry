[snap]: https://github.com/intelsdi-x/snap
[snap_rel]: https://github.com/intelsdi-x/snap/releases
[collectd]: https://github.com/collectd/collectd
[collectd_rel]: https://collectd.org/wiki/index.php/Version_5.5
[scollector]: http://bosun.org/scollector/
[bosun_rel]: https://github.com/bosun-monitor/bosun/releases
[tcollector]: https://github.com/OpenTSDB/tcollector
[tcollector_rel]: https://github.com/OpenTSDB/tcollector/releases
[diamond]: https://github.com/python-diamond/Diamond
[diamond_rel]: https://github.com/python-diamond/Diamond/releases
[telegraf]: https://github.com/influxdata/telegraf
[telegraf_rel]: https://github.com/influxdata/telegraf/releases
[metricsd]: https://github.com/josegonzalez/metricsd
[statsd]: https://github.com/etsy/statsd
[statsd_rel]: https://github.com/etsy/statsd/releases
[ceilometer]: https://github.com/openstack/ceilometer
[ceil_rel]: https://github.com/openstack/ceilometer/releases


# what we talk about when we talk about telemetry
The goal of this repository is to have a shared definition of telemetry. We can then differentiate telemetry tools. I hope you'll help.

## What is telemetry?
**My working definition:** Telemetry captures data from multiple sources, aggregates it, and publishes it in a consumable format. What happens after you collect and publish the information is beyond the scope of telemetry.

## Comparison
Telemetry frameworks are often conflated with entire monitoring solutions. I would like to clarity the differences.

### Overview
| Tools                               | Release Status                   | Default Interval | Collection Model | Written In | Client Libraries                            |
|:------------------------------------|:---------------------------------|:-----------------|:-----------------|:-----------|:--------------------------------------------|
| [Snap][snap]                        | Beta ([0.17.0][snap_rel])        | 1 second         | pull             | Go         | C++, Python                                 |
| [collectd][collectd]                | Released ([5.5][collectd_rel])   | 10 seconds       | pull             | C          | No                                          |
| Bosun's [scollector][scollector]    | Beta ([0.5.0][bosun_rel])        | 1 second         | pull             | Go         | No                                          |
| OpenTSDB's [tcollector][tcollector] | Released ([1.3][tcollector_rel]) | 15 seconds       | pull             | Python     | No                                          |
| [diamond][diamond]                  | Released ([4.0][diamond_rel])    | 300 seconds      | pull             | Python     | No                                          |
| [telegraf][telegraf]                | Released ([1.0][telegraf_rel]    | 10 seconds       | pull             | Go         | No                                          |
| [metricsd][metricsd]                | None                             | 30 seconds       | pull             | Go         | No                                          |
| [statsd][statsd]                    | Beta ([0.8.0][statsd_rel])       | N/A              | push             | JavaScript | [Many](https://github.com/etsy/statsd/wiki) |
| [Ceilometer][ceilometer]            | Released ([7.0.0][ceil_rel])     | 10 minutes       | pull             | Python     | No                                          |


TODO >> everything below here.

### Details
| Collect from multiple sources? | Able to Process data? | Publish to multiple sources? | Custom Resolution? | Timestamps? | Metric Identity? | Notifications? |


Runs on:
| Ubuntu | RedHat | Windows |


Requires Reboots for?
| Config change | Update of metrics | Update to endpoints published to | version upgrade |
|:--------------|:------------------|:---------------------------------|:----------------|
|               |                   |                                  |                 |

Include:
 * Metric Identity (Source)
 * Metric Values (Counters, Gauges, Percntiles, Nominal, Ordinal, Interval, Ratio)
 * Timestamps
 * Custom Resolution (6s, 6m)
 * Latency (after reading, how long before we can act on them?)
 * Spooling (persist dropping of metrics when endpoint is unavailable)

Sensing: /proc, /sys, syscalls(1)
Collection: while(true);
Analysis: Summing
 and sorting
Alerting: Sort to top
Visualization: ordered
 lists, dynamic sorting
Storage: none
Configuration:
 runtime shortcuts

Nagios

Sensing:
Subprocesses and plugins, LOTS of plugins
Collection:
Centralized scraping
Support for forwarding metrics
Analysis: At sensing time
Alerting:
Configurable alarms and emails
Visualization:
Basic graphs of check results
Dependency chains

Ganglia

Sensing:
gmond on nodes
extensions/plugins
Collection:
multicast, UDP, TCP polls
Analysis:
value_threshold
external (nagios)
Storage: rrdtool/rrdcached
Alerting: N/A
Visualization: ganglia-web


Sensu

Sensing: Arbitrary JSON emitters “Checkers”
Collection: RabbitMQ JSON event bus
Analysis:
Handlers
Storage: N/A
Alerting:
Handlers
Visualization: N/A


ELK

Sensing:
Deployable log thrower
Collection:
MQ (Redis)
Analysis:
Indexer
Storage:
ElasticSearch
Alerting: N/A
Visualization:
Kibana (ES)

OpenTSDB

Sensing:
Custom clients
Collection:
TSD RPC
Analysis:
External
Storage:
Complete storage layer
Alerting: N/A
Visualization: N/A

Graphite

Sensing:
DIY, name+value
Collection:
Custom messaging protocol
Analysis: N/A
Storage: Carbon+Whisper
file-per-metric
Alerting: N/A
Visualization:
Static config of complex graphs

## Going Beyond Telemetry

Sensors -> Telemetry -> Persistence -> Learning -> Visualization -> Notification -> Alerting

## "The Stacks"

There are a few maturing visions of a complete solution that goes from Telemetry all the way to Alerting.  

| Stack Name | Sensors  | Logging | Telemetry     | Persistence | Querying | Visualization | Notification | Alerting |
|:-----------|:---------|:--------|:--------------|:------------|:---------|:--------------|:------------------------|
| Raintank   | :x:      | Snap    | Graphite      | Grafana     | Grafana  | Grafana       | Grafana                 |
| ELK        | Logstash | Beats   | Elasticsearch | ES          | Kabana   |               |                         |
| Prometheus |          |         |               |             |          |               |                         |
| Zabbix     |          |         |               |             |          |               |                         |
| Netflix    |          |         |               |             |          |               |                         |
| VMware     |          |         |               |             |          |               |                         |

Open Source?
Enterprise Support?


Downsampling, filtering, aggregation

## Resources

What I made:
* [What I Mean By Telemetry](https://medium.com/intel-sdi/what-i-mean-by-telemetry-b3e1718a6ef8#.ptrr4n607) by [@mjbrender](https://github.com/mjbrender)
* [Making Telemetry A Snap With Intel’s Open Framework](http://packetpushers.net/podcast/podcasts/datanauts-033-making-telemetry-snap-intels-open-framework/) podcast ft [@mjbrender](https://github.com/mjbrender)

That I've reviewed:
* 2012 [The State of Open Source Monitoring](https://speakerdeck.com/obfuscurity/the-state-of-open-source-monitoring) by [Jason Dixon](https://twitter.com/obfuscurity)
* 2013 [A Working Theory of Monitoring](https://www.usenix.org/sites/default/files/conference/protected-files/dickson.pdf) by [Caskey L. Dickson](http://twitter.com/caskey)
* [RFC: What is Monitoring](https://docs.google.com/document/d/1ghi-2L44Hwcg3YFpGv-_SU_3ho2zWkkXaENbsxxpSLs/edit#) by [Heinrich Hartman](https://twitter.com/HeinrichHartman)
* https://collectd.org/features.shtml

That I need to explore:
* [Monitoring is Dead: Long Live Monitoring](https://github.com/grepory/monitorama2016) by [grepory](http://twitter.com/grepory)




Clean up later:
15 seconds for tcollector found here - http://opentsdb.net/docs/build/html/user_guide/utilities/tcollector.html
Collectd calls the resolution "Interval" and is 10s - https://collectd.org/wiki/index.php/Interval
diamond default value is here - http://diamond.readthedocs.io/en/latest/Getting-Started/Configuration/
Ceilometer doesn't have documentation on the default interval but I found this: https://ask.openstack.org/en/question/5882/how-to-change-the-polling-period-of-ceilometer/
