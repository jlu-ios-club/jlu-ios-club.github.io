---
layout: post
title:  "Swift-字典-按Key排序和按Value排序"
author: "陆子旭"
date:   2019-03-29
desc: ""
keywords: "Swift"
categories: [Code]
tags: [Swift,Tips]
icon: fa-apple
---

利用闭包，非常黑科技。
```swift
let dict = ["27":"w","15":"t","36":"b"]
let keys = dict.sorted(by: {$0.0 < $1.0})
let values = dict.sorted(by: {$0.1 < $1.1})
print(keys)
print(values)
```

[参考](https://www.jianshu.com/p/da294a0b2e48)