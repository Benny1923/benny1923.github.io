---
title: Ltayer2.0 錯誤修正 (Ltayer2.0 bug fix)
tags:
  - Ltayer
  - Ltayer bug fix
  - Ltayer 錯誤修正
id: '63'
categories:
  - - 其他
date: 2015-06-15 10:30:19
---

有沒有用過LTAYER? 謎之聲:誰會沒事自己架網站，就為了LTAYER啊? 就作者之一的「[電腦故我在](https://blog.allenchou.cc/)」站長:[Allen Chou](https://allenchou.cc/)所說:它是一款網路桌面 使用php語言編成，現行版本2.0([GitHub有這專案的源碼](https://github.com/licson0729/Ltayer)) 這裡有關於LTAYER的一系列文章([按我](https://blog.allenchou.cc/category/ltayer/))   某天我在網路上無意見到了這專案(2015.5.20) 好奇把他抓下來，裝到伺服器上 發現它....它....它....它根本是DSM UI有夠漂亮的啦! 但這都不是重點<Benny式標準「以上廢文」

* * *

  今天是來發修補檔案的: 緣由: 某天我在控制台看到「伺服器資訊」這個按鈕 「唉喲!不錯喔，還可以檢視伺服器資訊」 但是當我看到這按鈕[![47a9b8012770038a800e8b3ac0c72390[1]](https://blog.bennyling.cc/wp-content/uploads/2015/06/47a9b8012770038a800e8b3ac0c723901.png)](https://blog.bennyling.cc/wp-content/uploads/2015/06/47a9b8012770038a800e8b3ac0c723901.png) 不安的預感就出現了 結果我就很直覺的用\[get\]去鑽漏洞 結果就很自然的還真的被解(?) 正想去向作者們求救 結果就看到這個 [![Ltayer](https://blog.bennyling.cc/wp-content/uploads/2015/06/Ltayer.jpg)](https://blog.bennyling.cc/wp-content/uploads/2015/06/Ltayer.jpg)   #已死專案 那多麼令人絕望的消息...(跪 算了，我自己來 現在把一部份的bug修補好了 已發現bug(且已修復)的內容如下:

1.  sysinfo.php使用get(?act=phpinfo)原不須登入即可檢視php探針內容。現已修正為需要管理員權限
2.  Apps中的notepad可不須任何權限去 檢視/編輯/刪除 其他使用者的資料或新增一筆資料。現在必須為「擁有者」才能對內容進行操作

基本上都是跟使用get不需要帳號權限有關 以上 變更(修復)的檔案:

1.  admin/sysinfo.php
2.  apps/notepad/destory.php
3.  apps/notepad/edit.php
4.  apps/notepad/new.php
5.  apps/notepad/show.php
6.  database/database.php \*註:由於此檔案關係到LTAYER和MySQL資料庫的聯繫，若你已經安裝過了，請先將裡面的 "MySQL資料表名稱" "使用者名稱" "使用者密碼" "資料庫所在位址" 填入，否則將會變成全新安裝(全新安裝不再此限)

全部都是跟get不需要權限的錯誤檔案下載(只包含修補檔案，完整網站/原始碼需去[LTAYER的Github](https://github.com/licson0729/Ltayer)下載) [按我下載(google drive)](https://bit.ly/1Gn4t4x)

> MD5: fc78f01ba209a2221664087c63797c8f SHA-1: 420300011b21404623d951c8ad100bc20b8eee3c

目前還沒有發現其他bug 如果你發現了新的bug，可以在下面留言跟我說 (有意思想接手LTAYER) 雖然作者好像已經完成了部分ver2.1 但感覺作者好像沒甚麼動力 所以我想試著用LTAYER2.0為基礎進行下一代LTAYER的開發(雖然我code的能力不是很好) 不過在這之前，我會不定期地發布錯誤修正(bug fix)   那期待下一篇文章吧!