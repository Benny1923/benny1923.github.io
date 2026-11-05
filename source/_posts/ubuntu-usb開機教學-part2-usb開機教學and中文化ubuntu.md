---
title: Ubuntu-USB開機教學-Part2-USB開機教學and中文化Ubuntu
tags:
  - Live USB
  - Ubuntu
  - UNetbootin
  - 中文化
id: '8'
categories:
  - - Ubuntu
date: 2013-12-26 10:50:29
---

大家好，繼上次寫Bolg好像很久了ㄝ<--謎之聲:原來你知道...

這是有原因的，因為這次主題跟BIOS有關係，所以要用到攝影機，啊我沒有所以要去借...(又像上次又被巴<--沒梗了?)

好啦，進入今天的正題【USB開機教學and中文化Ubuntu】

先來看我好不容易拍好的「高畫質」相片<--謎之聲:你去借的相機畫質可真高啊

[![BIOS-1](https://farm4.staticflickr.com/3817/11564113734_b7b2142283_b.jpg)](https://www.flickr.com/photos/107928128@N03/11564113734) 

圖文解說又到啦

對，就是這個時候，按下\[F12\]

蝦?你說你是用別的廠牌，那麼希望[這個連結](https://www.lmgtfy.com/?q=%E5%90%84%E5%BB%A0%E7%89%8CBIOS+USB%E9%96%8B%E6%A9%9F)可以幫上你一點忙(別的廠牌可略過下張圖及說明)

再來是第二階段

[![BIOS-2](https://farm6.staticflickr.com/5503/11564341696_bf92d1294c_b.jpg)](https://www.flickr.com/photos/107928128@N03/11564341696) 

現在出現的是你要從哪裡開機，按「↑」或「↓」來選擇你的隨身碟

我記得我的隨身碟名字叫 JetFlash Transcend 8GB USB Device... (後面數字忘了)

接下來...

[![UNetbootin BIOS](https://farm6.staticflickr.com/5494/11564489276_6e5c142698_b.jpg)](https://www.flickr.com/photos/107928128@N03/11564489276) 

如你所見，這個就是UNetbootin的開機管理程式

如果你在這裡有幾秒不理它了話，它會進入預設「Default」的選項

「Default」就是以桌面模式進行開機，開機後的Ubuntu跟安裝版的畫面一樣，更重要的是，如果你用UNetbootin製作開機碟的系統是Ubuntu，這個選項可以讓你存在裡面的檔案不會消失，然而我們可以利用這個原理來製作中文化Ubuntu，而不會又因重新開機而回歸英文介面，詳情請見[Ubuntu-USB開機教學-Part1](https://sln98106.pixnet.net/blog/post/29578666)

至於其他的選項的話，我就不多做說明啦，請各位自行摸摸看 <--謎之聲:明明就是你不會

再來，就對我個人來說最痛苦的時候了XD

[![ubuntu-start oem](https://farm8.staticflickr.com/7432/11581690063_b3bd9f4081_b.jpg)](https://www.flickr.com/photos/107928128@N03/11581690063) 

這個畫面，讓我至少看它有10分鐘以上，我在上一篇有說過:「建議大家使用USB3.0容量大於8G的隨身碟來開機，不然，用它來開機時，速度會讓你想...」

因為我沒錢，只有一支2.0的隨身碟，所以我就...了 <--謎之聲:你重頭到尾都沒說會發生啥啊!!

[![Screenshot from 2013-12-25 18:30:34](https://farm6.staticflickr.com/5521/11582973564_67a0866137_b.jpg)](https://www.flickr.com/photos/107928128@N03/11582973564)

經過漫長的開機後，終於開好機了

一切都就緒了，那我們就開始「中文化」吧！

 [![Screenshot from 2013-12-25 18:39:50](https://farm3.staticflickr.com/2837/11582966444_4ce124a361_b.jpg)](https://www.flickr.com/photos/107928128@N03/11582966444) 

首先，我們要先連上網路（本人以ADSL作說明），這樣才能下載語言包啊，點選上方長的像「棒球場」的圖示（？），選單最下面的選項「Edit Connection...」

按下「add」

[![Screenshot from 2013-12-25 18:40:05](https://farm3.staticflickr.com/2864/11582636315_27dabd94cc_b.jpg)](https://www.flickr.com/photos/107928128@N03/11582636315)

下拉至「DSL」，按「Create...」

接下來彈出的視窗本人沒有截圖不過我大致說明一下：

「Connection Name」是你新增的連線的名字

「Userame」是你的ADSL用戶帳號

「Password」是你的ADSL密碼

都打好後，按下「Save...」儲存連線設定，在按一次長的像「棒球場」的圖示，選擇你新增的連線的名字

連上網路後，我們就開始下載中文包吧

[![Screenshot from 2013-12-25 18:37:48](https://farm3.staticflickr.com/2837/11582642495_cf975d0ff4_b.jpg)](https://www.flickr.com/photos/107928128@N03/11582642495) 

首先打開控制台，點選右上角的齒輪，找到「System Settings...」點下去就可以打開控制台

打開控制台後，選擇「Language support」

[![Screenshot from 2013-12-27 11:41:29](https://farm3.staticflickr.com/2819/11582624235_aeb1b7a9f1_b.jpg)](https://www.flickr.com/photos/107928128@N03/11582624235) 

打開語言設定視窗後，會彈出兩個視窗，扁寬的視窗會顯示在上面，它的意思是指要下載其他的語言或翻譯工具嗎?不過我們今天的目的是要使用繁體中文，所以不需要，按「Remind Me Later」略過

[![Screenshot from 2013-12-25 10:54:42](https://farm4.staticflickr.com/3767/11582854613_46eb43d88c_b.jpg)](https://www.flickr.com/photos/107928128@N03/11582854613) 

按「Install/Remove Languages...」

[![Screenshot from 2013-12-25 10:49:48](https://farm6.staticflickr.com/5491/11582652745_ff377c7704_b.jpg)](https://www.flickr.com/photos/107928128@N03/11582652745) 

找到「Chinese(traditional)」的選項，把它後面的框框給打勾，然後按「Apply Changes」

[![Screenshot from 2013-12-25 10:50:10](https://farm8.staticflickr.com/7428/11583441326_bd3c327b90_b.jpg)](https://www.flickr.com/photos/107928128@N03/11583441326) 

等一下，它在下載及安裝中文語言包，先去做其他的事吧!

[![Screenshot from 2013-12-25 10:55:00](https://farm3.staticflickr.com/2871/11583438756_6ca2c7e2bd_b.jpg)](https://www.flickr.com/photos/107928128@N03/11583438756) 

接下來把上方的清單中的「漢語(臺灣)」拖到最上方，按下「Apply System-Wide」套用至全系統，如上圖

切到「Regional Format」的標籤，下拉選項至「漢語(臺灣)」，按下「Apply System-Wide」套用至全系統

再重新啟動電腦

[![螢幕擷圖存為 2013-12-25 19:46:14](https://farm4.staticflickr.com/3719/11582951454_0a0359ebd4_b.jpg)](https://www.flickr.com/photos/107928128@N03/11582951454) 

按下「更新名稱(U)」後，恭喜你，中文化Ubuntu了，享受它吧
