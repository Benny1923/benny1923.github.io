---
title: Ubuntu-USB開機教學-Part1-USB開機碟製作，UNetbootin使用教學
tags:
  - Live USB
  - Ubuntu
  - UNetbootin
id: '7'
categories:
  - - Ubuntu
date: 2013-12-12 12:56:31
---

大家好，今天是一個重要的日子

是什麼日子呢?

就是......就是......就(講到一半就被巴)

好痛...就是我第一次寫部落格啦

第一次就寫教學文，好像有點自大ㄝ...

不管了，直接進入正題

今天要教的是 Ubuntu USB開機碟的製作

先準備好一支隨身碟(本人使用的是USB2.0的創見8G隨身碟，不過建議大家使用USB3.0容量大於8G的隨身碟來開機，不然，用它來開機時，速度會讓你想...)

向大家介紹一款神器UNetbootin

[![ub6-e](https://farm6.staticflickr.com/5474/11350942734_30f758f0d2_b.jpg)](https://www.flickr.com/photos/107928128@N03/11350942734)

你問我這東西是啥?這東西可神了，它提供一個介面化USB開機碟的製作介面

要製作USB開機碟就靠他啦，先把它下載下來吧，點一下紅框選起來的第一個(for Windows)的圖片  [有請神奇傳送門](https://unetbootin.sourceforge.net/)

接下來的這個動作可做也可不做

[![ub2-e](https://farm4.staticflickr.com/3702/11350942064_c84da65eb4_b.jpg)](https://www.flickr.com/photos/107928128@N03/11350942064)

[上圖網址傳送門(台灣論壇)](https://www.ubuntu-tw.org/modules/tinyd0/)    [Ubuntu原文官方網站](https://www.ubuntu.com/)

接下來是圖文解說:

1 是它的發行板，預設選項是桌面版本，USB開機碟也是用這版本。

2 是版本號，本人在此用的是13.04來解說，不過台灣論壇提供的是最新版本(上)和長期支援的版本(下)。

3 是電腦架構，本人在此沒有做太深入的研究，總之，選擇你要用USB開機碟開機的電腦位元就好了。

4 是下載選項，直接按\[開始下載\]等一下就開始下載了，如果需要用BT種子下載的就把上述選項打勾再按\[開始下載\]。

一切都準備好了嗎?那我們就開始吧!

[![ub1-e](https://farm3.staticflickr.com/2851/11350994433_f528b728b1_o.jpg)](https://www.flickr.com/photos/107928128@N03/11350994433)

1 是你要安裝在USB中的作業系統，右邊是版本號。(如果沒有去下載ISO檔的要選擇這裡)

2 是簡介區，如果 1 沒有選任何東西的話，會顯示UNetbootin的簡介。

3 是直接透過上個步驟下載下來的ISO檔來安裝在USB中。

4 是假如說你用USB來開機時儲存檔案時在USB的作業系統裡，但USB Live僅僅只是暫時存在USB裡，等到關機時它就會把資料刪除了，這時就需要設定它了，但注意這只對Ubuntu有用而已，還有請計算排除Ubuntu的檔案大小(約為0.79GB=808.96MB)還剩下多少空間可用，建議留一些空間，不要配置的剛剛好。

5 是設定你要安裝在哪一支隨身碟裡的，當所有東西都設定好了之後，就按下\[確定\]吧!

[![ub4](https://farm8.staticflickr.com/7429/11350837665_0bf6f9b1eb_o.jpg)](https://www.flickr.com/photos/107928128@N03/11350837665)

這時就開始把Ubuntu安裝到你的隨身碟中了，請注意這時可能會沒有回應，但也不要關閉它，它還沒有當掉

 [![ub5](https://farm4.staticflickr.com/3831/11350903226_6b56b86351_o.jpg)](https://www.flickr.com/photos/107928128@N03/11350903226) 

當出現這個畫面時，代表恭喜你了，你已經做好了一支USB開機碟了，你可以用USB來開機了。

最後，告訴大家一件很可怕的事...

那就是，不管你從哪裡的到的Ubuntu的ISO檔(如台灣論壇、原文官方)以及用UNetbootin直接下載來製作的USB開機碟，用它來開機時都會是英文(我英文很爛，好可怕啊...XDD)

所以，下一節，我要來教大家用今天製作的USB開機碟來開機，以及，盡可能地把它給中文化。敬請期待[Ubuntu-USB開機教學-Part2-USB開機教學and中文化Ubuntu](https://blog.bennyling.cc/8/)

註:使用USB開機時，你存在USB中的資料在非USB開機模式時打開隨身碟，只會看到Ubuntu的系統檔案，並不會看到你的檔案，同道理，在非USB開機模式所存在USB的檔案，在USB開機模式時也看不到，請注意。
