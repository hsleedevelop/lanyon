---
layout: post
title: Functional, lazy protocol
description: Functional, lazy protocol
category: swift
tags: [swift]
---

source: [https://medium.com/swift-programming/using-lazy-to-delay-computation-8aa4ea236d0a](https://medium.com/swift-programming/using-lazy-to-delay-computation-8aa4ea236d0a)

{% highlight swift %}

/// Avoid creating multiple layers of `LazySequence` wrapper.
/// Anything conforming to `LazySequenceProtocol` is already lazy.
extension LazySequenceProtocol {
    /// Identical to `self`.
    public var lazy: Self { get }
}


let array2 = [1, 2, 4, 5, 3, 7]
let element = array2.map{ $0 * 2 }[3] //7 times
print(element)


let array3 = [1, 2, 4, 5, 3, 7]
let element3 = array3.lazy.map{ $0 * 2 }[3] //2 times
print(element3)

{% endhighlight %}
