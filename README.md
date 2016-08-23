# what we talk about when we talk about telemetry
The goal of this repository is to have a shared definition of telemetry. We can then differentiate telemetry tools. I hope you'll help.

## What is telemetry?
DEFINITION TBD

**My working definition:** Telemetry captures data from multiple sources, aggregates it, and publishes it in a consumable format. What happens after you collect and publish the information is beyond the scope of telemetry.

## Comparison

| framework | Default Resolution | What's most important? | ? | written in | language specific |
|:----------|:-------------------|:-----------------------|:--|:-----------|:------------------|
| snap      | 1 second           |                        |   | Go         | N                 |
| collectd  | 10 seconds         |                        |   | C          |                   |
| diamond   |                    |                        |   | Python     | Y                 |
| telegraf  |                    |                        |   | Go         |                   |

## Resources

What I made:
* [What I Mean By Telemetry](https://medium.com/intel-sdi/what-i-mean-by-telemetry-b3e1718a6ef8#.ptrr4n607) by [@mjbrender](https://github.com/mjbrender)
* [Making Telemetry A Snap With Intel’s Open Framework](http://packetpushers.net/podcast/podcasts/datanauts-033-making-telemetry-snap-intels-open-framework/) podcast ft [@mjbrender](https://github.com/mjbrender)

That I've reviewed:
* [A Working Theory of Monitoring](https://www.usenix.org/sites/default/files/conference/protected-files/dickson.pdf) by [Caskey L. Dickson](http://twitter.com/caskey)
* [RFC: What is Monitoring](https://docs.google.com/document/d/1ghi-2L44Hwcg3YFpGv-_SU_3ho2zWkkXaENbsxxpSLs/edit#) by [Heinrich Hartman](https://twitter.com/HeinrichHartman)
* https://collectd.org/features.shtml

That I need to explore:
* [Monitoring is Dead: Long Live Monitoring](https://github.com/grepory/monitorama2016) by [grepory](http://twitter.com/grepory)
