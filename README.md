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
[cadvisor]: https://github.com/google/cadvisor
[cadvisor_rel]: https://github.com/google/cadvisor/releases
[beats]: https://github.com/elastic/beats/tree/master/metricbeat
[beats_rel]: https://beats-nightlies.s3.amazonaws.com/index.html?prefix=metricbeat


# what we talk about when we talk about telemetry
The goal of this repository is to have a shared definition of telemetry. We can then differentiate telemetry tools. I hope you'll help.

## What is Telemetry?
**My working definition:** Telemetry captures data from multiple sources, aggregates it, and publishes it in a consumable format. What happens after you collect and publish the information is beyond the scope of telemetry.

## Comparison
Telemetry frameworks are often conflated with entire monitoring solutions. I would like to clarity the differences.

### Overview
| Tools                               | Release Status                   | Default Interval | Collection Model | Written In | API  |
|:------------------------------------|:---------------------------------|:-----------------|:-----------------|:-----------|:-----|
| [Snap][snap]                        | Beta ([0.17.0][snap_rel])        | 1 second         | Pull             | Go         | Yes  |
| [collectd][collectd]                | Released ([5.5][collectd_rel])   | 10 seconds       | Pull             | C          | No   |
| Bosun's [scollector][scollector]    | Beta ([0.5.0][bosun_rel])        | 1 second         | Pull             | Go         | Yes  |
| OpenTSDB's [tcollector][tcollector] | Released ([1.3][tcollector_rel]) | 15 seconds       | Pull             | Python     | Yes  |
| [diamond][diamond]                  | Released ([4.0][diamond_rel])    | 300 seconds      | Pull             | Python     | Yes? |
| [Telegraf][telegraf]                | Released ([1.0][telegraf_rel]    | 10 seconds       | Pull             | Go         | No?  |
| [statsd][statsd]                    | Beta ([0.8.0][statsd_rel])       | N/A              | Push             | JavaScript | Yes  |
| [Ceilometer][ceilometer]            | Released ([7.0.0][ceil_rel])     | 10 minutes       | Pull             | Python     | Yes  |
| [cAdvisor][cadvisor]                | Beta ([0.24][cadvisor_rel])      | 1 second         | Pull             | Go         | Yes  |
| Elastic's [metricbeats][beats]      | Alpha ([6.0.0][beats_rel])       | 10 seconds       | Pull             | Go         | No?  |
| [metricsd][metricsd]                | None                             | 30 seconds       | Pull             | Go         | No   |

I will focus only on projects that have public releases from this point forward.

### About Collecting and Publishing
The core functionality of telemetry frameworks.

| Tools                               | Collect from multiple sources? | Able to Process data? | Publish to multiple sources? | Custom Interval?   | Multiple Intervals? |
|:------------------------------------|:-------------------------------|:----------------------|:-----------------------------|:-------------------|:--------------------|
| [Snap][snap]                        | :white_check_mark:             | :white_check_mark:    | :white_check_mark:           | :white_check_mark: | :white_check_mark:  |
| [collectd][collectd]                | :white_check_mark:             | :x:                   |                              | :white_check_mark: | :x:                 |
| Bosun's [scollector][scollector]    | :white_check_mark:             |                       |                              |                    |                     |
| OpenTSDB's [tcollector][tcollector] |                                |                       |                              |                    |                     |
| [Diamond][diamond]                  |                                |                       |                              |                    |                     |
| [Telegraf][telegraf]                |                                |                       |                              |                    |                     |
| [statsd][statsd]                    |                                |                       |                              |                    |                     |
| [Ceilometer][ceilometer]            |                                |                       |                              |                    |                     |
| [cAdvisor][cadvisor]                |                                |                       |                              |                    |                     |
| Elastic's [metricbeats][beats]      |                                |                       |                              |                    |                     |

### About Operational Use
The cost of using these tools, from an operations perspective, is important to comparing them.

### About Operational Ease of Use

* **Requires Reboots for?**

| Tools                               | Config change | Update of metrics | Update to collectors | Update to publishers | version upgrade |
|:------------------------------------|:--------------|:------------------|:---------------------|:---------------------|:----------------|
| [Snap][snap]                        | Yes           | No                | No                   | No                   | Yes             |
| [collectd][collectd]                | Yes           | Yes               | Yes                  | Yes                  | Yes             |
| Bosun's [scollector][scollector]    |               |                   |                      |                      |                 |
| OpenTSDB's [tcollector][tcollector] |               |                   |                      |                      |                 |
| [Diamond][diamond]                  |               |                   |                      |                      |                 |
| [Telegraf][telegraf]                |               |                   |                      |                      |                 |
| [statsd][statsd]                    |               |                   |                      |                      |                 |
| [Ceilometer][ceilometer]            |               |                   |                      |                      |                 |
| [cAdvisor][cadvisor]                |               |                   |                      |                      |                 |
| Elastic's [metricbeats][beats]      |               |                   |                      |                      |                 |



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
