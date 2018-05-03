---
layout: post
title: closure, cast constraint
description: closure, cast constraint
category: swift
tags: [swift]
---

You can only upcast to a parent type:

var closure : (Subclass) -> () = {
    (first : Superclass) in
}
you cannot downcast to a subclass
