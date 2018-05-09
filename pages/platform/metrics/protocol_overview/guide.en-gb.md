---
title: Overview of supported protocols
slug: protocol-overview
excerpt: Get an overview on supported protocols for Metrics
section: Protocol
order: 1
---

**Last updated 7th May, 2018**

## Choose yours, no vendor lock-in!

> Metrics is protocol agnostic, it means that you can push your data with OpenTSDB, and query it with Warp10 or vice versa.
> Metrics doesn't enforce you to a proprietary protocol. Instead, we believe the plurality of existing protocols from Open Source solutions can be used to achieve Pushing and Querying the platform.

### Supported protocols
Each protocol provides different capabilities. Some will be easier than others but may have less features. We've tried to summary them with this simple table :

|Protocol|Push|Query|Protocol documentation|Features|Corresponding Open Source project|
|---|---|---|---|---|---|
|Graphite|<i class="fas fa-check"></i>|<i class="fas fa-check"></i>|[Metrics Graphite](#graphite_desc)|<i class="fas fa-star"></i>|[http://graphiteapp.org/](http://graphiteapp.org/){.external}|
|InfluxDB|<i class="fas fa-check"></i>|<i class="fas fa-times"></i>|[Metrics Influx](#influx_desc)|<i class="fas fa-star"></i>|[https://github.com/influxdata/influxdb](https://github.com/influxdata/influxdb){.external}|
|Metrics2.0|<i class="fas fa-check"></i>|<i class="fas fa-times"></i>|[Metrics 2.0 spec](#opentsdb_desc)|<i class="fas fa-star"><i class="fas fa-star">|[http://metrics20.org/](http://metrics20.org/){.external}|
|OpentSDB|<i class="fas fa-check"></i>|<i class="fas fa-check"></i>|[Metrics OpenTSDB](#opentsdb_desc)|<i class="fas fa-star"><i class="fas fa-star">|[http://opentsdb.net/](http://opentsdb.net/){.external}|
|Prometheus|<i class="fas fa-check"></i>|<i class="fas fa-check"></i>|[Metrics Prometheus](#prom_desc)|<i class="fas fa-star"></i><i class="fas fa-star"></i>|[https://prometheus.io/](https://prometheus.io/){.external}|
|SQL|<i class="fas fa-times"></i>|<i class="fas fa-times"></i>|[Metrics SQL](#sql_desc)|||
|Warp10|<i class="fas fa-check"></i>|<i class="fas fa-check"></i>|[Metrics Warp10](#warp_desc)|<i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>|[http://www.warp10.io/](http://www.warp10.io/){.external}|

Most of the protocols don't include **authentification**, so **you need to add the tokens in the Basic Auth field.**

 > If you're wondering which protocol to choose, here is a simple guideline :
 >
 > - You want to push json? -> `OpenTSDB`
 > - You want to instrument your code? -> `Prometheus SDK` & `Beamium`
 > - You want powerful analytics? -> `Warp10` & `WarpScript`
 > - You want BI tools integration like Tableau, Power BI, Qlik? -> `SQL`



### Authentification and endpoints
Metrics has builtin security to secure your data. In the Start section you've learnt where to get them from the manager. We've generated a default pair of **tokens** :

- a **READ** token to Query
- a **WRITE** token to Push Data

Except for Warp10 (where it's provided as a specific Header for push and in the DSL payload for queries), this token will be used as the password in the [Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication){.external}.

Most of the protocols are available through HTTPS endpoints. Here's the logic for pushing:

**`https://token:[write token]@[protocol].[region].metrics.ovh.net`**

For example :  https://token:cersX8.P5X_4Zv...LEXV_hoXuKcn_BRp2eqp7@opentsdb.gra1.metrics.ovh.net

The user in the basic authenfication is discarded.
