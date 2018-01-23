---
layout: post
title: RxOptional Example
category: swift
tags: [swift]
---

Observable<[Notice]>.of(self.notifications)
    .replaceNilWith([])
    .bind(to: tableView.rx.items(cellIdentifier: "NotificationTableViewCell", cellType: NotificationTableViewCell.self)) { indexPath, notice, cell in
        cell.notice = notice
    }.disposed(by: disposeBag)
