---
layout: post
title:  "Swift-正则表达式类-NSRegularExpression"
author: "陆子旭"
date:   2019-03-21
desc: ""
keywords: "Swift"
categories: [Code]
tags: [Swift,Tips]
icon: fa-apple
---

# Swift-正则表达式类-NSRegularExpression

```swift
   /**
     正则表达判断是否含有结果值
     - parameter pattern: 一个字符串类型的正则表达式
     - parameter str: 需要比较判断的对象
     - returns: 返回布尔值判断结果
     - warning: 注意匹配到结果的话就会返回true，没有匹配到结果就会返回false
     */
    class func regex(pattern:String, str:String) -> Bool {
        let regex = try! NSRegularExpression(pattern: pattern, options:[NSRegularExpression.Options.caseInsensitive])
        let resultNum = regex.numberOfMatches(in: str, options: NSRegularExpression.MatchingOptions(rawValue: 0) , range: NSMakeRange(0, str.characters.count))
        if resultNum>=1 {
            return true
        }
        return false
    }


```

```swift
   /**
     正则表达式获取目的值
     - parameter pattern: 一个字符串类型的正则表达式
     - parameter str: 需要比较判断的对象
     - imports: 这里子串的获取先转话为NSString的[以后处理结果含NS的还是可以转换为NS前缀的方便]
     - returns: 返回目的字符串结果值数组(目前将String转换为NSString获得子串方法较为容易)
     - warning: 注意匹配到结果的话就会返回true，没有匹配到结果就会返回false
     */
    class func regexGetSub(pattern:String, str:String) -> [String] {
        var subStr = [String]()
        let regex = try! NSRegularExpression(pattern: pattern, options:[NSRegularExpression.Options.caseInsensitive])
        let results = regex.matches(in: str, options: NSRegularExpression.MatchingOptions.init(rawValue: 0), range: NSMakeRange(0, str.characters.count))
        //解析出子串
        for  rst in results {
            let nsStr = str as  NSString  //可以方便通过range获取子串
            subStr.append(nsStr.substring(with: rst.range))
            //str.substring(with: Range<String.Index>) //本应该用这个的，可以无法直接获得参数，必须自己手动获取starIndex 和 endIndex作为区间
        }
        return subStr
    }


```

[参考](https://blog.csdn.net/qq_14920635/article/details/77689830)