---
layout: post
title: Protocol Extension - function's implementation cannot be overridden by a subclass
description: Protocol Extension - function's implementation cannot be overridden by a subclass
category: swift
tags: [swift]
---

[source](https://bugs.swift.org/browse/SR-103)


Protocol Extension: function's implementation cannot be overridden by a subclass  

A function(x') is not called that we thought If there is following conditions.  

A protocol(A) is defined a function(x).  
A has implement of x in the protocol extension.  
A class(B) is implement A, but doesn't have implement x.  
A subclass(C) is inheritance B, and have implement x(x').  
A instance of C typed A, and call x.  

```
// Defined protocol.
protocol A {
    func a() -> Int
}
extension A {
    func a() -> Int {
        return 0
    }
}

// A class doesn't have implement of the function.
class B: A {}

class C: B {
    func a() -> Int {
        return 1
    }
}

// A class has implement of the function.
class D: A {
    func a() -> Int {
        return 1
    }
}

class E: D {
    override func a() -> Int {
        return 2
    }
}

// Failure cases.
B().a() // 0
C().a() // 1
(C() as A).a() // 0 # We thought return 1.

// Success cases.
D().a() // 1
(D() as A).a() // 1
E().a() // 2
(E() as A).a() // 2
```
