---
title: 'windows 10 linux子系統: 玩壞了?重裝就好啦'
tags:
  - lxrun
  - windows 10
  - windows 10 bash
  - windows 10 linux
id: '433'
categories:
  - - Windows
date: 2016-08-07 13:53:41
---

上一篇我猜測每個windows的使用者的linux環境可能都是獨立的 既然是獨立的，重新安裝當然是沒有問題啦 Benny我在更新後開啟linux子系統功能後兩個小時內就把它玩壞了(X 我是怎樣玩壞的: 就亂調整etc中的設定 亂編譯一堆自己寫的code，還有阿...(夠了!沒人想知道 oh抱歉離題了 重新安裝之前我們先了解一個指令: lxrun 這個是針對管理linux子系統安裝、設定及移除的指令 我們先輸入lxrun /? 看看裡面有什麼 [![lxrun](https://blog.bennyling.cc/wp-content/uploads/2016/08/lxrun.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/lxrun.png) 我們可以看到主要有install uninstall setdefaultuser 和 update 四個參數 /install: 安裝參數，有/y的子參數(可選)，可以自動接受使用協議。用法: lxsrun /install /y /uninstall: 移除安裝參數，有/full /y兩個子參數(可選)，/full 為完整解除安裝，連同home root等使用者資料夾都刪除，/y 為不經二次確認直接執行指令。用法: lxrun /uninstall /full /y /setdefaultuser: 設定一啟動bash後預設登入的使用者，若指定的使用者不存在，會自動新增一個。用法: lxrun /setdefaultuser \[使用者名稱\] /update: 這我說不出來哪裡怪，很像apt-get update，但又不是。??? 總而言之是更新指令。用法: lxrun /update 所我們只需要下這兩個指令: lxrun /uninstall /full /y lxrun /install /y 就完成重新安裝了 歐對了，這是題外話 你知道linux子系統類似於ping這種發送icmp封包指令是會發生錯誤的 然後還有不能架設server(所有port都有問題) ... 我去找找解決方案