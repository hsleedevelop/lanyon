---
layout: post
title: Async DispatchQueue Usage
description: Async DispatchQueue Usage
category: swift
tags: [swift]
lang: ko
---

{% highlight swift %}

class func requestDeterminingPermission(completion: BSTClosure.emptyAction? = nil) {

    let permissionSet = PermissionSet(Permission.defaultSet)
    //        guard let _ = permissionSet.permissions.filter({ $0.status == .notDetermined }).first else {
    //            return
    //        }

    let queue = DispatchQueue(label: "PermissionManagerQueue")

    for (index, permission) in permissionSet.permissions.enumerated() {

        queue.async {
            if permission.status == .notDetermined {//권한 체크 이력 확인,
                permission.request({ (status) in  //각 권한별 요청
                    logDebug(status)
                })
            }
        }
    }

    queue.async {
        completion?()
    }
}

{% endhighlight %}
