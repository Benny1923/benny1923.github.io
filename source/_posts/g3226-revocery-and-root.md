---
title: Sony Xperia XA1 Ultra(G3226) 刷TWRP Recovery+Root
tags:
  - G3226
  - Recovery
  - root
  - Xperia XA1 Ultra
id: '598'
categories:
  - - Anodroid 開發、刷機大小事
date: 2020-01-12 13:39:54
---

hi Android Root我又回來了，隨著手機功能越來越完善，Root這件事似乎變得沒那必要，但若想玩一些新奇的功能，那Root依然那裡等你，雖然近年來利用漏洞一鍵root的App的消失使root沒那麼容易，但對於熟悉刷機的你我都知道，製造商留了一扇窗給你...

老樣子

免責聲明: 刷機有風險，解鎖失保固，操作前請再三評估，作者一概不負責

好了不必多說，你需要的東西我列好了:

1.  一隻Xperia XA1 Ultra(我手上這支型號是G3226，雙卡版，但理論上叫這名字都可以用)
2.  一條傳輸線
3.  adb fastboot工具和相關驅動
4.  boot.img和recovery.img(詳見文末參考自第一條)
5.  對解鎖、刷機等名詞相關基礎名詞之認識(對，如果你是第一次玩可能得去其它地方爬文)
6.  記得備份，解鎖會清除資料

#### 解鎖手機

打開手機的電話，輸入`*#06#`看第一組IMEI號碼，記下來然後關閉，輸入下一組號碼`*#*#7378423#*#*`進入工程模式，選`Servie info > Configuration`找到`Rooting status`下面那行，確定它寫著`Bootloader unlock allowed: Yes`就可以繼續進行下去，如果是No那就不用玩了。

打開設定，進入`系統 > 關於手機`，對著`版本號碼`連按7次回到`系統`找到`開發者選項`，打開`USB偵錯`和`OEM解鎖`(可能需要輸入手機密碼，如果你有設定的話)

接上傳輸線，打開console(小黑窗)(注意!這邊假設你已經知道adb和fastboot的環境配置和小黑窗用法，不知道的可以去google"adb fastboot用法"，如果我寫了會分掉其他優秀作者的曝光度)  
輸入:  
`adb devices`  
多留意一下手機，會有需要授權的提示，同意後，再輸入一次上面指令，確認裝置ID旁邊的狀態是`device`而不是`unauthorized`才能進行下一步

輸入:  
`adb reboot bootloader`  
你的手機回重開進fastboot模式，LED會是藍燈，先不要碰它

去[Sony解鎖網站](http://bit.ly/36Hehc2)最下面有`Select your device:`，選`Xperia XA1 Ultra`，再往下，在`Enter IMEI, IDID or MEID`中輸入剛剛記下的IMEI，下面第一個和第二個打勾，按`Submit`，會給你一組解鎖碼，複製下來

回到小黑窗，輸入:  
`fastboot oem unlock 0x解鎖碼`  
確定訊息沒出現FAILED就解鎖了

#### 刷Recovery

接下來的部分是從文末參考那簡單翻譯過來的，任何我說明不清楚的部分可以去看看

參考那邊沒有G3226的boot和recovery，但你可以抓G3212的版本(個人正在用)，基本上都是同一手機，只是在不同國家有其它型號。

在fastboot模式輸入:  
`fastboot flash boot boot.img`  
沒有FAILED就是成功了  
然後重啟:  
`fastboot reboot`  
重開好後你應該需要重新設定手機，然後再去開發者模式設定USB除錯(adb)  
都處理好了輸入:  
`adb reboot bootloader`  
(注意手機授權請求)  
進fastboot後輸入:  
`fastboot flash recovery recovery.img`  
沒有FAILED就是成功了  
最後拔掉傳輸線

#### 進recovery

開機時同時按電源按鈕和音量向下鍵，向下鍵要按到手機震一下還有LED亮紫(?)燈才能放手

這邊要是遇到需要輸入密碼請直接無視，然後去Wipe那邊選Format Data輸入yes即可

#### 刷Root

到這邊應該已經沒有老手在了吧，刷完Recovery基本就自由了  
刷Root的簡短概述就是:

1.  下載[Magisk](http://bit.ly/2Tdb2oK)然後放進手機
2.  進Recovery選Install
3.  選剛剛放進去的卡刷包(在 /sdcard 下)
4.  完成收工 ， 重新開機

參考或翻譯自:  
1.[https://forum.xda-developers.com/xa1-ultra/development/g3221-built-sources-t3622886](http://bit.ly/37WCk6Z)