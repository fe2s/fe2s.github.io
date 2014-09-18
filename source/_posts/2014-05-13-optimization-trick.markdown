---
layout: post
title: "optimization trick"
date: 2014-05-13 21:48:28 +0300
comments: true
categories: storm, optimization
---

An interesting optimization trick from [Storm](http://storm.incubator.apache.org/) internals which reminded me some algorithmic problem(see in the end).

For those who haven't heard about Storm, in short it's a distributed realtime computation system. Scalable, fault tolerant and guarantees that every message is fully processed.

<!-- more -->

<img src="{{ root_url }}/images/storm/storm.png"  />

The incoming tuple(message in Storm terminology) is processed by the bolt(processing node). Bolt can spawn more tuples which in their turn are further processed by succeeding bolt(s). So you end up with a tuple tree (directed acyclic graph actually).

The question is how to guarantee that every tuple is fully processed, i.e if some bolt fails, the tuple is replayed. We have to acknowledge when intermediate tuple created and when it's processed. With huge tuple trees, tracking the entire tree state is memory expensive.

Strom designers decided to use an elegant trick which allows to know when tuple is fully processed with O(1) memory.

Tuple is associated with a random 64bit id. The tree state is also 64bit value called 'ack val'. Whenever tuple is created or acknowledged, just `XOR` tuple id with ack val. When ack val becomes 0, the tree is fully processed. Yes, there is a a small probability of mistake, at 10K acks per second, it will take 50,000,000 years until a mistake is made. And even then, it will only cause data loss if that tuple happens to fail.

Now the algorithmic problem. Given an array of integer numbers. Each number except one appears exactly twice. The remaining number appears only once in the array, find this number with one iteration and O(1) memory. Easy, yay!



