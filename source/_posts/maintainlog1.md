---
title: 網站維護日誌+CF的worker妙用
tags:
  - CloudFlare
  - linux
  - raspberry pi
id: '535'
categories:
  - - 其他
date: 2019-09-15 19:05:21
---

好久沒有寫blog了，上一次是多久前阿...

有看過關於本站頁的都知道(沒看過?右上角連結點一下)  
我的網站是架在一台rpi 2上的  
到今天依然是它在服務著我以及各位  
自從網站架成後，四年過去了，之前對他不聞也不問，直到昨天心血來潮  
「要不我把它重灌?」  
的確，隨著新版本的php7出現，而我還在用php5，在安全及速度上都說不過去  
雖然平常會apt update && apt upgrade -y  
但升級php7這件事，我真的不想去動它，沒為甚麼，單純我懶  
要改config有的沒的(藉口，到處都是藉口)

終於我在昨天下定決心把rpi 2的系統全部重裝，終於可以升級php7啦  
先解決維護頁面問題，原本我是打算把文章全快取成靜態頁，這樣就不會影響維護時的流量  
but 這實在是太麻煩了，還有我網站根本沒有流量(36篇文章真的沒什麼流量)，所以用一段文字來顯示維護中就好  
然後我需要一個靜態頁伺服器放顯示維護中的html  
等等...我的pi等等要下線，那誰來負責這件事?  
CF有一個叫 Workers 的功能(要開加速)，你可以設定條件網址去觸發worker，worker 執行用javascript編寫的功能

```js
addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

/\*\*
 \* Fetch and log a request
 \* @param {Request} request
 \*/
async function handleRequest(request) {
 
  let modifiedHeaders = new Headers()
 
  modifiedHeaders.set('Content-Type', 'text/html; charset=utf-8')
  modifiedHeaders.append('Pragma', 'no-cache')
 
 
  //Return maint page if you're not calling from a trusted IP
  if (request.headers.get("cf-connecting-ip") !== "123.123.123.123") 
  {
    // Return modified response.
    return new Response(maintPage, {
      headers: modifiedHeaders
    })
  }
  else //Allow users from trusted into site
  {
    //Fire all other requests directly to our WebServers
    return fetch(request)
  }
}

let maintPage = "網站維護中...";
```

上面這段程式會把所有請求攔截下來，傳回"網站維護中..."的文字，除非你的ip是123.123.123.123，那你可以正常瀏覽網站

再來是備份和重灌  
先把wordpress的文章和圖片導出，以防萬一，sqldump也跑個  
確定東西備份好，關機，拔SD卡  
我看著rpi 2想：「這東西竟然能連續通電4年?」  
然後就是重寫映像，放進去開機，然後ssh連上去  
在這邊奉勸各位系統剛灌好，第一件事就是:

改密碼!!

全世界都知道raspbian的預設帳密是 pi / raspberry  
以前有個朋友我剛幫他裝完系統，離開前有提醒要改密碼，隔天就被駭去挖礦了  
我實在是不知道該對他說什麼好，只好再幫他重裝一次(工具人貼紙+1)

然後 nginx php7-fpm mariadb(mysql) 裝好  
"簡單"設定一下， wordpress 下載回來  
把setup流程跑完，文章導回來，大功告成囉!  
另外我也換了個佈景主題，希望各位喜歡

最後  
新版的編輯器好不習慣啊，天啊我不在這段時間wordpress都改了些什麼  
更新完後使用舊編輯器的文章語法高亮有問題，我會盡快修正  
但對那些不能修復的呢，咳咳，我也不知道怎麼辦

參考資料: [https://medium.com/clouddevops/cloudflare-no-maintenance-mode-still-a-maintainace-mode-d0d088d414c1](https://medium.com/clouddevops/cloudflare-no-maintenance-mode-still-a-maintainace-mode-d0d088d414c1)