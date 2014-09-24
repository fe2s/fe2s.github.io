---
layout: post
title: "Code Refactoring Detection"
date: 2012-03-21 15:13:35 +0300
comments: true
categories: code review, diff, merge, refactoring
---

An idea of feature I would love to see in code review and diff/merge tools.

Consider you are reviewing code changes or making 3-way merge where among various things a name of some method has changed. Personally I don’t want to go through tens of files and check that all usages of method changed accordingly.

I would like to see it in more declarative way. One phrase saying ‘method `Foo.bar()` has changed to `Foo.bar2()`’ would be enough. Imagine you could accept this particular change and now tool ignores it making the whole picture clearer.

Say for  static object-oriented languages I can imagine a number of refactoring types  where this could be useful - method extract, all kind of renames, replacing inheritance with delegation, replacing constructor with factory methods and so on.

How difficult would it be to implement semantic aware diff on top of Intellij IDEA ?
