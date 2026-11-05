---
title: 'windows 10 linux子系統: 如何存取linux環境中的資料'
tags:
  - windows 10 bash
  - windows 10 linux
id: '419'
categories:
  - - Windows
date: 2016-08-06 20:13:39
---

在上一篇我也不知道我在說甚麼做什麼的測試中，我說明了windows磁碟機在linux環境中是以資料夾的型態出現的 這一篇我要說的是linux環境中的資料會出現在windows的哪兒呢? 這真的非常的特別 路徑: C:\\Users\\\[windows使用者名稱\]\\AppData\\Local\\lxss 放在AppData中... 這難道說明每個使用者的linux環境都是獨立的!? [![wow](https://blog.bennyling.cc/wp-content/uploads/2016/08/wow.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/wow.png) 由上圖可看見: rootfs 是linux環境中的 / (看起來好像嵌入式linux XD) 其他的東西就是使用者資料拉 home裡面就是使用者的家目錄 root就是root的家目錄 另外要注意的是:rootfs裡面也有home root mnt等資料夾，但是還是以lxss這一層的目錄為主，所以檔案別放錯地方喔 bash.ico 是ubuntu的logo 估計是程式開啟後再去讀取的 所以在這裡容許我玩耍一下... [![www](https://blog.bennyling.cc/wp-content/uploads/2016/08/www.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/www.png) 還真的可以改啊XDDDD 個人化設定，嗯...印象加分 不會是等到特定節日微軟會改這個給我們驚喜吧，好我想太多了