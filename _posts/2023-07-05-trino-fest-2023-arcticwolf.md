---
layout: post
title: "AWS Athena (Trino) in the cybersecurity space"
author: "Anas Shakra, Ryan Duan"
excerpt_separator: <!--more-->
image: /assets/blog/trino-fest-2023/ArcticWolf.png
show_pagenav: false
---

Arctic Wolf Networks, a cybersecurity company that provides security monitoring
to cyber threats, is one of the companies that have recently switched to using
AWS Athena as a new and efficient service to query their data using Trino. AWS
Athena is a serverless, interactive analytics service built on open-source
frameworks that runs on Trino, supporting open table and file formats and
providing a simplified, flexible way to analyze petabytes of data where it
lives. Senior software developer Anas Shakra from Arctic Wolf Networks gave a
talk at [Trino Fest 2023]({% post_url 2023-06-20-trino-fest-2023-recap %})
detailing their switch to AWS Athena and how "queries that took hours with old
solution now take around a minute today". Tune in to the talk or you can read
the recap!

<!--more-->

{% youtube WCuJaW7zC8k %}

## Recap

At Arctic Wolf, data access use-cases fall under three categories: investigations,
compliance, and customer self-serve platform. The process of preparing the data
follows an established pattern of starting with datastore, performing an
operation to filter or transform the data, and then outputting the data in some
format like a CSV or JSON, depending on the client needs. Arctic Wolf's custom
legacy service was unable to match the growing service demand and had four main
problems:

* Optimized for breadth over depth
* Struggles to handle growing service demand
* Proprietary query language
* Complicated design

This compelled Anas' team to find a different and improved service: Trino as
provided by AWS Athena.

They had four main objectives for the new service: defined access patterns,
performant at scale, user-friendly, and deterministic pricing. AWS Athena
satisfied these objectives, while also providing numerous benefits such as using
a powerful query engine, being purposefully built for large datasets, using SQL
syntax, and having a clear pricing structure. However, with these benefits come
some drawbacks for Athena. These includes being subject to quota limits, having
suboptimal file sizes for their system, and being unable to control access
sufficiently. Anas addresses this by using log queries that resolves these three
main impediments. As next step, Anas is considering switching to a self-managed
Trino deployment for more control with the same performance gains.

Want to learn more about log queries that they use? Check out Anas' explanation
in the video!

## Share this session

If you thought this talk was interesting, consider sharing this on Twitter,
Reddit, LinkedIn, HackerNews or anywhere on the web. If you think Trino is awesome,
[give us a 🌟 on GitHub <i class="fab fa-github"/>](https://github.com/trinodb/trino)!