---
layout: post
title:  "Swift-UITextView"
author: "陆子旭"
date:   2019-03-24
desc: ""
keywords: "Swift"
categories: [Code]
tags: [Swift,UITextView]
icon: fa-apple
---

# Swift-UITextView

事情起源于在我码编译原理代码的时候，想实现在设备上显示不会自动换行的大量文字。即必须允许可以上下左右拖拽TextView，直接使用一个TextView貌似没法实现（就是我没找到方法），于是需要一个ScrollView作为TextView的容器，具体方法如下：（无需多少英文水平，就不翻译了）

1. So, firstly, we need a longlonglong String, right?

```swift
let displayStr ="1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20n1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20"
```

2. Assume we have a UIScrollView which is linked by @IBOutlet or got by calling the .viewWithTag(xxx). We will let it be named as scroll :

3. it's time to get the size of our string, here is a key function we'll use it :

Oh! i almost forget to define what kind of Font ( this's a crucial parameter ) we will use, and what is the max-size of our string's size

```swift
let maxSize = CGSizeMake(9999, 9999)
let font = UIFont(name:"Menlo", size: 16)!
//key function is coming!!!
let strSize = (displayStr as NSString).boundingRectWithSize(maxSize, options: NSStringDrawingOptions.UsesLineFragmentOrigin, attributes: [NSFontAttributeName : font], context: nil)
```

4. OK, now we can put the string into a textView, you need to programmatically create a new UITextView, so that we can define the frame which is identical to the string's size(Oh, maybe a little bigger :D) :

```swift
let frame = CGRectMake(0, 0, size.width+50, size.height+10)
let textView = UITextView(frame: frame)
textView.editable = false
textView.scrollEnabled = false//let textView becomes unScrollable
textView.font = font
textView.text = displayStr
```

5. Back to our scroll, we will set its contentSize :

```swift
scroll.contentSize = CGSizeMake(size.width, size.height)
```

6. Finally, addSubview :scroll.addSubview(textView)

You can see, textView is embed in a scrollView, which allow it to scroll with 2 directions.

[参考](https://ask.helplib.com/c/12417391)