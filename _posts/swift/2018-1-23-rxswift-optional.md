---
layout: post
title: RxSwift Code Snippet
description: RxSwift Code Snippet
category: swift
tags: [swift]
---


{% highlight swift %}

Observable<[Notice]>.of(self.notifications)
    .replaceNilWith([])
    .bind(to: tableView.rx.items(cellIdentifier: "NotificationTableViewCell", cellType: NotificationTableViewCell.self)) { indexPath, notice, cell in
        cell.notice = notice
    }.disposed(by: disposeBag)


subject = BehaviorSubject(value: self.notifications)
subject?.bind(to: tableView.rx.items(cellIdentifier: "NotificationTableViewCell", cellType: NotificationTableViewCell.self)) { indexPath, notice, cell in
    cell.notice = notice
    }.disposed(by: disposeBag)

self.subject?.onNext(self.notifications)

{% endhighlight %}
