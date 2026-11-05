---
title: 'windows 10 linux子系統: 如何存取windows中的資料'
tags:
  - windows 10 bash
id: '401'
categories:
  - - Windows
date: 2016-08-06 11:56:59
---

從昨天我的windows 10更新後，我就一直在研究這項功能的優缺點 當然讓我發現了一件事: 檔案存取 windows 10中linux似乎和windows是在兩個不同的...環境?(我不知道我在說啥 在linux環境中，windows的磁碟機是以掛載...阿不對，是資料夾的形式存在 為甚麼我會這樣說呢?請看下圖 [![ismountornot](https://blog.bennyling.cc/wp-content/uploads/2016/08/ismountornot.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/ismountornot.png) 我們可以看見，我的windows中有3個磁碟機，分別為C D T 分別對應至linux環境中 /mnt 底下的三個 c d t 資料夾 我們輸入df -h觀察該資料夾是否是對應/dev底下任何一個檔案 沒有 ls /dev 也沒有任何發現 因此推導出一個結論: 磁碟機是以資料夾的型態出現在linux環境中

### 讀取測試

首先我們在windows C:\\ 底下建立一個文字檔 benny.txt 隨便輸入些內容 然後在linux環境下，輸入cat /mnt/c/benny.txt [![readtest](https://blog.bennyling.cc/wp-content/uploads/2016/08/readtest.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/readtest.png) 測試成功!

### 寫入測試

在linux環境下輸入nano /mnt/c/benny.txt 編輯並存檔試試(我不喜歡vi，真的) [![nano](https://blog.bennyling.cc/wp-content/uploads/2016/08/nano.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/nano.png) [![ask](https://blog.bennyling.cc/wp-content/uploads/2016/08/ask.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/ask.png) [![path](https://blog.bennyling.cc/wp-content/uploads/2016/08/path.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/path.png) 唉呀!失敗了 [![fail](https://blog.bennyling.cc/wp-content/uploads/2016/08/fail.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/fail.png) 為甚麼呢? 因為C:\\是受寫入保護的，所以linux環境無法對其寫入(很安全的設計) 那我們試試 D:\\ 吧 輸入nano /mnt/d/benny.txt [![ductnano](https://blog.bennyling.cc/wp-content/uploads/2016/08/ductnano.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/ductnano.png) [![ductask](https://blog.bennyling.cc/wp-content/uploads/2016/08/ductask.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/ductask.png) [![ductpath](https://blog.bennyling.cc/wp-content/uploads/2016/08/ductpath.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/ductpath.png) 成功了!! [![success](https://blog.bennyling.cc/wp-content/uploads/2016/08/success.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/success.png) 以上就是全部的說明了 由於這是新功能，很多東西我還沒摸透，如果有高人看到這篇有錯，還請不要吝嗇多指教