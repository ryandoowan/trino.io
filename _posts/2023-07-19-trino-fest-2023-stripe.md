---
layout: post
title: "Inspecting Trino on ice"
author: "Kevin Liu, Ryan Duan"
excerpt_separator: <!--more-->
image: /assets/blog/trino-fest-2023/Stripe.png
show_pagenav: false
---

Stripe is an online payment processor that facilitates online payments for
digital native merchants. They use Trino to facilitate ad hoc analysis, enable
dashboarding, and provide internal API in order for services to utilize Trino to
query information. In Kevin Liu's session at [Trino Fest 2023]({% post_url
2023-06-20-trino-fest-2023-recap %}), he details the power of Trino connectors
and their usefulness to databases.

<!--more-->

{% youtube PSGuAMVc6-w %}

## Recap

Trino is the foundational infrastructure on which other apps and
services are built upon. In Kevin's words, "I call Trino the Swiss army knife in
the data ecosystem." At Stripe, they use Iceberg tables extensively and want to
migrate away from Hive. Some problems with the Iceberg CLI is that it requires
an internal developer machine that accesses their data, which is painful to use
for them. The output is also in JSON format, which is not human readable.
However using the Trino Iceberg connector, it can replace some of the
functionalities of the Iceberg CLI.

Unfortunately, there was no way to grant table property information from the
Trino Iceberg connector, because they were using an older version. Thus, they
use the Trino PostgreSQL connector to inspect table metadata from Hive
metastore. This connector reads Hive metastore's databases directly with Trino.
With the connector, they have all the information about the data warehouse and
can do a lot more analysis of the data.

They also use Trino to inspect Iceberg usage patterns. They log every Trino
query using the Trino event listener and store that in a PostgreSQL database.
This gives the full information of every query that has ever run through Trino.
This allows them to use the Trino connector to connect to the database and read
events. Starburst actually has a version of this functionality called the
Starburst query logger. This query metadata enrichment enables multitude of
auditing, debugging, and optimization use cases.

In the future, they plan to use Trino as a validation framework and for Iceberg
table maintenance, and optimize tables based on read patterns.

## Share this session

If you thought this talk was interesting, consider sharing this on Twitter,
Reddit, LinkedIn, HackerNews or anywhere on the web. If you think Trino is awesome,
[give us a 🌟 on GitHub <i class="fab fa-github"/>](https://github.com/trinodb/trino)!