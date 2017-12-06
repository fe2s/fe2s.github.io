---
layout: page
title: "How we built InsightEdge. Slides and talk recording"
date: 2017-12-06 12:36
comments: true
sharing: true
footer: true
---

Sharing my slides and talk recording (in Russian) from JavaDay 2016 conference. 

In this talk I discuss how we built an open-source Spark distribution [http://insightedge.io](http://insightedge.io) that runs on top of in-memory database. 

<!-- more -->

The agenda of the talk: 

* a need of hybrid transactional and analytical processing
* an overview of in-memory datagrid features
* how we designed InsightEdge RDD partitions to make it scalable
* implementation of Spark DataSource API to support DataFrame/SQL
* optimization techniques: predicates push-down and columns pruning
* how InsightEdge can run 30 times faster that regular Spark
* designing API with Scala, the good and unpleasant parts
* extending Spark API with geo spatial queries
* testing with Docker

Video recording (in Russian):

<iframe width="560" height="315" src="https://www.youtube.com/embed/RGoIlpB13U0?rel=0" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>

Slides:

<script async class="speakerdeck-embed" data-id="67f31bb62d8e42feafdcc1c24db17524" data-ratio="1.41436464088398" src="//speakerdeck.com/assets/embed.js"></script>
