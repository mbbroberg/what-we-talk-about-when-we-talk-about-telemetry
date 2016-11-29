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
The goal of this repository is to have a shared definition of telemetry. By working on a common vocabulary, we can then differentiate tools in an unbiased way. I hope you'll help.

## What is Telemetry?
**My working definition:** Telemetry captures data from multiple sources, aggregates it, and publishes it in a consumable format. What happens after you collect and publish the information is beyond the scope of telemetry.

### Parts of Telemetry Frameworks
This gets tricky. I can only start with what I'm curious about, which includes:

* operational ease of use (API and restarts required)
* collection from multiple sources (aka sensors)
* interval of collection (aka resolution)
* publishing to multiple sources (aka sources)

## Comparison
Telemetry frameworks are often conflated with entire monitoring solutions. I would like to clarity the differences. To do so, I'm going to focus on only the telemetry portion of lots of tools.

### Overview
| Tools                               | Release Status                   | Collection Model | Written In | API  |
|:------------------------------------|:---------------------------------|:-----------------|:-----------|:-----|
| [Snap][snap]                        | Beta ([0.17.0][snap_rel])        | Pull             | Go         | Yes  |
| [collectd][collectd]                | Released ([5.5][collectd_rel])   | Pull             | C          | No   |
| Bosun's [scollector][scollector]    | Beta ([0.5.0][bosun_rel])        | Pull             | Go         | Yes  |
| OpenTSDB's [tcollector][tcollector] | Released ([1.3][tcollector_rel]) | Pull             | Python     | Yes  |
| [diamond][diamond]                  | Released ([4.0][diamond_rel])    | Pull             | Python     | Yes? |
| [Telegraf][telegraf]                | Released ([1.0][telegraf_rel]    | Pull             | Go         | No?  |
| [statsd][statsd]                    | Beta ([0.8.0][statsd_rel])       | Push             | JavaScript | Yes  |
| [Ceilometer][ceilometer]            | Released ([7.0.0][ceil_rel])     | Pull             | Python     | Yes  |
| [cAdvisor][cadvisor]                | Beta ([0.24][cadvisor_rel])      | Pull             | Go         | Yes  |
| Elastic's [metricbeats][beats]      | Alpha ([6.0.0][beats_rel])       | Pull             | Go         | No?  |
| [metricsd][metricsd]                | None                             | Pull             | Go         | No   |

I will focus only on projects that have public releases from this point forward.

### About Collecting and Publishing
The core functionality of telemetry frameworks.

| Tools                               | Default Interval | Custom Interval?   | Multiple Intervals? | Collect from multiple sources? | Able to Process data? | Publish to multiple sources? |
|:------------------------------------|:-----------------|:-------------------|:--------------------|:-------------------------------|:----------------------|:-----------------------------|
| [Snap][snap]                        | 1 second         | :white_check_mark: | :white_check_mark:  | :white_check_mark:             | :white_check_mark:    | :white_check_mark:           |
| [collectd][collectd]                | 10 seconds       | :white_check_mark: | :x:                 | :white_check_mark:             | :x:                   |                              |
| Bosun's [scollector][scollector]    | 1 second         | :white_check_mark: |                     |                                |                       |                              |
| OpenTSDB's [tcollector][tcollector] | 15 seconds       |                    |                     |                                |                       |                              |
| [Diamond][diamond]                  | 300 seconds      |                    |                     |                                |                       |                              |
| [Telegraf][telegraf]                | 10 seconds       |                    |                     |                                |                       |                              |
| [statsd][statsd]                    | N/A              |                    |                     |                                |                       |                              |
| [Ceilometer][ceilometer]            | 10 minutes       |                    |                     |                                |                       |                              |
| [cAdvisor][cadvisor]                | 1 second         |                    |                     |                                |                       |                              |
| Elastic's [metricbeats][beats]      | 10 seconds       |                    |                     |                                |                       |                              |

### About Operational Use
The cost of using these tools, from an operations perspective, is important to consider.

### About Operational Ease of Use

* **Requires Reboots for?**

| Tools                               | New metrics | New collectors | New publishers | Version upgrade | Config change |
|:------------------------------------|:------------|:---------------|:---------------|:----------------|:--------------|
| [Snap][snap]                        | No          | No             | No             | Yes             | Yes           |
| [collectd][collectd]                | Yes         | Yes            | Yes            | Yes             | Yes           |
| Bosun's [scollector][scollector]    |             |                |                |                 |               |
| OpenTSDB's [tcollector][tcollector] |             |                |                |                 |               |
| [Diamond][diamond]                  |             |                |                |                 |               |
| [Telegraf][telegraf]                |             |                |                |                 |               |
| [statsd][statsd]                    |             |                |                |                 |               |
| [Ceilometer][ceilometer]            |             |                |                |                 |               |
| [cAdvisor][cadvisor]                |             |                |                |                 |               |
| Elastic's [metricbeats][beats]      |             |                |                |                 |               |


## Moar!

The above is a list I'm playing around with. Do you find it helpful? Give it a star to let me know :star: so I know to keep improving it for you. Want to add information? Open a PR following the format above and be sure to support the details with links either in the PR notes or in [Notes.md](Notes.md).

## Resources

What I made:
* [What I Mean By Telemetry](https://medium.com/intel-sdi/what-i-mean-by-telemetry-b3e1718a6ef8#.ptrr4n607) by [@mjbrender](https://github.com/mjbrender)
* [Making Telemetry A Snap With Intel’s Open Framework](http://packetpushers.net/podcast/podcasts/datanauts-033-making-telemetry-snap-intels-open-framework/) podcast ft [@mjbrender](https://github.com/mjbrender)

That I've reviewed:
* 2012 [The State of Open Source Monitoring](https://speakerdeck.com/obfuscurity/the-state-of-open-source-monitoring) by [Jason Dixon](https://twitter.com/obfuscurity)
* 2013 [A Working Theory of Monitoring](https://www.usenix.org/sites/default/files/conference/protected-files/dickson.pdf) by [Caskey L. Dickson](http://twitter.com/caskey)
* [RFC: What is Monitoring](https://docs.google.com/document/d/1ghi-2L44Hwcg3YFpGv-_SU_3ho2zWkkXaENbsxxpSLs/edit#) by [Heinrich Hartman](https://twitter.com/HeinrichHartman)

That I need to explore:
* [Monitoring is Dead: Long Live Monitoring](https://github.com/grepory/monitorama2016) by [grepory](http://twitter.com/grepory)
