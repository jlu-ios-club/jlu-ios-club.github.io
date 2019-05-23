---
layout: post
title:  "Swift-枚举-CaseIterable"
author: "陆子旭"
date:   2019-03-27
desc: ""
keywords: "Swift"
categories: [Code]
tags: [Swift,Tips]
icon: fa-apple
---

Swift 4.2 引入一个新的 protocol CaseIterable，它被用于合成简单枚举类型的 allCases 静态属性，代码如下：

```swift
    enum Weekday : String, CaseIterable {
        case monday, tuesday, wednesday, thursday, friday
    }

    print(Weekday.allCases)
```

所谓“简单枚举类型”，指的是不带关联值的枚举类型。所以，如果上述 Weekday 枚举声明成 enum Weekday : String, CaseIterable 的话（指定rawType），编译器也是能够自动合成的。

这样的功能可以使我们很方便的处理枚举的遍历。

本来想写个枚举的具体使用的，后来发现太多了，就贴个链接了：[枚举高级用法](https://www.jianshu.com/p/11f5b818cbfe)

[参考](https://www.jianshu.com/p/92b88e4525d1)