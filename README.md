# what we talk about when we talk about telemetry
The goal of this repository is to have a shared definition of telemetry. We can then differentiate telemetry tools. I hope you'll help.

## What is telemetry?
DEFINITION TBD

**My working definition:** Telemetry captures data from multiple sources, aggregates it, and publishes it in a consumable format. What happens after you collect and publish the information is beyond the scope of telemetry.


Sensors -> Telemetry -> Persistence -> Learning -> Visualization -> Notification -> Alerting 



## Comparison
Telemetry frameworks are often conflated with entire monitoring solutions. I've been reading up and hope to clarity the differences. 

| Tools                                            | Status     | Default Resolution | Model | ? | written in | language specific |
|:-----------------------------------------------------|:-----------|:-------------------|:------|:--|:-----------|:------------------|
| [Snap](https://github.com/intelsdi-x/snap)           | 1 second   | 1 second           | push  |   | Go         | N                 |
| [collectd](https://github.com/collectd/collectd)     | 10 seconds | 10 seconds         | push  |   | C          |                   |
| [Bosun](https://github.com/bosun-monitor/bosun)      |            |                    | push  |   |            |                   |
| [diamond](https://github.com/python-diamond/Diamond) |            |                    |       |   | Python     | Y                 |
| [telegraf](https://github.com/influxdata/telegraf)   |            |                    |       |   | Go         |                   |
| [metricsd](https://github.com/josegonzalez/metricsd) |            |                    |       |   | Go         |                   |
| [statsd](https://github.com/etsy/statsd)             |            |                    |       |   | JavaScript |                   |

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


## "The Stacks" 

There are a few maturing visions of a complete solution that goes from Telemetry all the way to Alerting.  

| Stack Name | Sensors | Logging | Telemetry | Persistence | Querying | Visualization | Notification | Alerting | 
|------|------|------|------|------|------|------|----|
| Raintank | :x: | Snap | Graphite | Grafana | Grafana | Grafana | Grafana | 
| ELK | Logstash | Beats | Elasticsearch | ES | Kabana | |
| Prometheus | 
| Zabbix | 
| Netflix |
| VMware | 

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
