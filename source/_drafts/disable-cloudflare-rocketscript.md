---
title: javascript無作用?也許是cdn的問題喔。取消rocketscript試試看吧
tags:
  - CDN
  - CloudFlare
  - javascript
  - rocketscript
id: '385'
categories:
  - - html/css/javascript
date: 2016-07-15 19:28:39
---

CDN(Content delivery network或Content distribution network，中譯: 內容傳遞網路) 是一種利用最靠近使用者的伺服器，將目的伺服器資料傳遞給使用者，達到加速的目的，另外還能有效抵禦Dos攻擊等優點 在眾多CDN服務商中，最知名的莫過 CloudFlare 啦 CloudFlare提供dns管理、cdn服務等眾多功能，免費方案其實已經能符合大多數人的需求了 #這不是業配文 但是，當開啟CloudFlare的cdn服務的時候，在某些情況，會使網站javascript無作用 這其實是CloudFlare的其中一個功能造成的問題   [![rockerloader](https://blog.bennyling.cc/wp-content/uploads/2016/07/rockerloader.png)](https://blog.bennyling.cc/wp-content/uploads/2016/07/rockerloader.png) 沒錯，就是這個「Rocket Loader™」導致的 這會讓javascript非同步載入 首先，以下這是修改前的javascript標籤(上:include 下:在標籤內):

<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<script type="text/javascript">
//你的程式碼
</script>

如果開啟了「Rocket Loader™」，用戶在瀏覽後，會變這樣子

<script data-rocketsrc="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js" type="text/rocketscript" data-rocketoptimized="true"></script>
<script type="text/rocketscript" data-rocketoptimized="true">
//你的程式碼
</script>

接下來你有兩個選擇: 1.關掉「Rocket Loader™」 這方法簡單多了，上面那張圖看到沒?把右邊那個選項改成off就好了。簡單吧 2.在HTML標籤 "<script>" 中加入屬性 data-cfasync="false" 這是一個高知識水準個屁的Blog，當然要教些高知識水準的東西啊 把"<script type="text/javascript">"中加入這個屬性 data-cfasync="false" 如下:

<script data-cfasync="false" src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<script data-cfasync="false" type="text/javascript">
//你的程式碼
</script>

這樣，你的javascript就不會非同步載入了   #買域名到現在才發現寫不到十篇文章