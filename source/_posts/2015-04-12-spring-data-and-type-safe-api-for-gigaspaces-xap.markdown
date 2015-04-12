---
layout: post
title: "Spring Data and type-safe API for GigaSpaces XAP"
date: 2015-04-12 21:21:13 +0300
comments: true
categories: GigaSpaces, XAP, Spring
---

Spring Data API with a number of fancy extensions is now available for GigaSpaces XAP. Check it out on [github](https://github.com/Gigaspaces/xap-spring-data)     

### Motivation: ###

- make it easy to use in-memory datagrid for those who already have experience with Spring Data APIs such as Spring Data MongoDB, JPA, Redis, etc. 
- significantly reduce the amount of boilerplate code required to implement data access layer
- reduce the amount of effort in switching from any Spring Data implementation to XAP
- catch API errors at compile time (type-safe API using QueryDSL)

<!-- more -->

## Features ##

- Spring configuration support using Java based @Configuration classes or XML namespace, filters support
- CRUD and Paging repositories extended with XAP specific features such as projections, change API, lease, take, etc
- repository for XAP Documents
- selectively exposing CRUD methods
- query methods (e.g. `findByNameAndAge`)
- custom methods
- common query lookup strategies
- property expressions
- special parameters handling including `Sort` and `Pageable`
- native XAP API support
- seamless integration with all native XAP features - persistence, transcations, event processing, security, indexes, lease, etc
- ability to work with multiple spaces
- QueryDSL integration to support type-safe API(queries, projection, change API)


## Getting Started
- documentation including 5-mins guide [http://docs.gigaspaces.com/sbp/spring-data.html](http://docs.gigaspaces.com/sbp/spring-data.html)
- [examples](https://github.com/Gigaspaces/xap-spring-data/tree/master/examples) and [sources](https://github.com/Gigaspaces/xap-spring-data)

