---
layout: post
title: "Java enums in distributed systems"
date: 2016-01-20 23:01:20 +0200
comments: true
categories: java distributed enum
---

Did you ever think about how `hashCode()` of `java.lang.Enum` implemented?

<!-- more -->

Surprisingly or not it's 

```java
public final int hashCode() {
  return super.hashCode();
}
```

it returns the `Object`'s `hashCode` which is an internal address of the object to a certain extend. From the first glance it totally makes sense since `Enum` values are singletons. 

Now imagine you are building distributed system. Distributed systems use `hashCode` to 

- determine which worker in a cluster should handle part of a huge job 
- determine which node in a cluster should store given item of dataset (e.g. in distributed cache)

 The same `Enum` instance would give you a different `hashCode` value in different JVMs/hosts, screwing up your Hadoop job or put/lookup in distributed storage. Just something I faced recently.




