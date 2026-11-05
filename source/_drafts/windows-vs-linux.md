---
title: Windows 和 Linux 的差異
tags: []
id: '102'
categories:
  - - Linux
  - - Windows
---

## windows(win7 or up ,以下簡稱win) 和 linux 的差異：

### 價錢(正版)：

win：3000～5000(個人用,商業版or win server可至數萬元以上)但是從win7 or up(正版)的系統升級至win10(正版)則免費 linux：大多數免費

### 原始碼開放狀態：

win：閉源(根據消息,microsoft已經開始將很久以前的win源碼(MS-DOS)開放了) linux：開源

### 硬體需求：

win：為求良好的視覺體驗及其他效能因素,故硬體需求較高 linux：硬體需求較低

不對,不能這樣講...

### 相同硬體條件下,剩餘的資源狀況

win：因許多系統服務執行,剩餘能使用的資源較少 linux：除非額外安裝服務,不然剩餘資源較win多

### 安裝方法：

win：GUI安裝,人性化,簡單 linux：GUI安裝,人性化,簡單(只有在部份linux衍生版本上)

### 桌面環境：

win：explorer.exe(所謂「IE」中的「E」<冷笑話,別理他) linux：不固定(由各linux衍生系統決定,有：KDE,GNOME...但也可能沒有桌面環境)

### 應用程式取得方式：

win：無限 <廢話 linux：無限 <廢話第二發

### 應用程式安裝方法：

win：我想大部分人的安裝方式都是：下一步到底,如果遇到使用(授權)條款是「我同意」吧...<所以到底有沒有人跟我一樣把使用條款(授權)讀完啊？ linux：打開你的終端(Terminal),又或者你已經在CLI環境下了 1.~$ sudo apt-get update <更新套件庫 2.~$ sudo apt-get install <package> (如果套件庫有的話) OR 1.~$ dpkg -i <package> (以上方法僅支援Debian及其衍生發行版,不然大多都是以以下方法安裝) 1.下載tar.gz格式的檔案($ wget <URL>) 2.~$ tar -zxvf <file> 3.~$ cd <dir> 4.dir$ ./configure <再這之前先確保需要的lib是否都到齊了 5.dir$ make <編譯檔案 (6.#make install) <安裝,可省略 #超複雜 (還有其他安裝方式如：rpm , yum等)

### 驅動程式的取得及安裝：

win：來源較多(開發商也多),安裝方便 linux：來源較少,安裝方式複雜<這次連我都不太清楚怎麼安裝了

### 硬體支援狀況：

win：絕大部分支援 linux：因硬體開發商大多只針對win開發驅動程式,對於linux較不重視,所以硬體支援較少,只能仰賴一些驅動的開源計畫

### 檔案系統支援：

win：支援FAT12/FAT16,FAT32/VFAT,NTFS linux：支援FAT12/FAT16,FAT32/VFAT,NTFS,ext2,ext3,ext4,NFS等

### 命令列介面：

win：cmd.exe(又名「命令提示字元」)和 Power shell <相信我,絕大部份的人都不知道自己的win裡有這東西,也不知道它可以做什麼 linux：Bash和sh等(無GUI,由tty執行,亦可使用X Terminal在X window執行)

### 相容：

win：有Cygwin和MinGW ,不過都是shell,都是CUI ,且執行方法是通過「事前」特別編譯過的.exe檔再交給linux指令集執行,理論上來說只能算移植 linux：有wine(此軟體有google協助改進),可執行.exe檔案(並非全部,依然得依賴wine內部函式庫),無論是CUI還是GUI ,都是即時轉譯

### 市場狀況：

win：世界75%以上的個人電腦採用win linux：主要應用於伺服器及超級電腦,伺服器市場市占率已達29%以上,嵌入式裝置/系統方面,我們所使用的android就是嵌入式linux,如今android裝置的市占率已達61.9%以上,另外,linux的嵌入式系統也應用於機上盒,路由器,防火牆等裝置

### 這裡值得一提的是linux的X Window系統：

普通win再執行一個有GUI的程式時,對顯示卡執行繪圖指令的路徑如下：程式>系統>驅動程式>顯示卡>>輸出至螢幕 但在linux環境下執行GUI程式卻不一樣：程式>X Window系統>系統>驅動程式>顯示卡>>輸出至螢幕 發現了嗎？linux再執行繪圖處理時,中間多了一道手續,沒錯,就是「X Window系統」 X Window系統 包含「伺服端」和「客戶端」,你以為出現「伺服端」這名詞就需要網路連線嗎？沒網路就不能使用嗎？其實不然,「伺服端」(以下稱為X Server)和「客戶端」(以下稱為X Client)是可以同時存在於一台電腦裡的,所以X Window是可以在離線下運作的,既然已經有了X Server了,那麼遠端裝置的X Client也可以連線至本機獲取X Server的資料,反之亦然 X Window的運作原理其實也很好懂,X Server負責接收來自「輸入單元」的資料(如：鍵盤,滑鼠等),再將資料傳送至X Client(應用程式端or遠端),X Client回饋資料至X Server,X Server再將資料輸出至輸出單元(如：顯示卡,音效卡等),或X Client(可能是本機,也可能是遠端) linux的桌面環境大多是透過X Window系統構成,這種方法的壞處就是應用程式到輸出單元中間多了一層X window(Application > X Client > X Server > Linux System > Device driver > Output device),這會導致執行效率降低,可能不適合在此平台執行需要及時畫面運算的程式(如：FPS遊戲)音效方便表現也不佳,改善的方法多半是將驅動程式直接包裝在linux的核心裡,但效能依然較win差 只有壞處嗎?不,好處還是有的,X Window系統不規範介面設計標準,使GUI並不像win一樣被約束,而是十分多變化 註：X window對於linux是可選套件,因此並非所有linux系統都有X window,伺服器版本的linux可能為求效能而將其移除

### 所以,挖掘機技術那家強？(誤linux和microsoft windows到底誰好呢？

以下內容可能有一點主觀,如果不想看怕引起反感的,請直接關閉此分頁;如果還想繼續看下去,就繼續看下去  

首先我們來比較一下桌機(PC)方面好了： Windows幾乎擁有壟斷市場的能力,為什麼?

想必是windows的GUI操作方式囉,多數操作都可以用滑鼠達成

那linux也有X window構成的GUI阿,也可以用滑鼠操作阿

哼!人家windows有宣傳,然而linux卻沒有

沒錯!linux的確是缺少宣傳,你有在任何廣告中看到linux嗎?

linux還有一個不及windows的地方

linux在系統更新上並沒有統一,有的衍生版甚至需要使用者來手動更新

然而widnows有自己的更新系統,名為windows update,但是由於此更新方式操作了許多系統服務,所以非常的消耗系統資源(CPU,記憶體怪獸

更新還不打緊,linux上的使用者幾乎無法避免接觸到終端,許多事情都必須使用終端才能完成

比方說剛剛的手動更新,就需要使用到終端了

結論:如果你是剛用linux新手的話,可以先裝windows,linux雙系統,等適應linux需要常接觸終端和指令了以後,還是繼續雙系統(搞屁),因為有些事還是只有windows做的來,不過可以將win設定成副系統,預設用linux開機

嵌入式裝置方面：

很明顯這次是linux贏了

linux的特性就是開源,易移植(還有不用錢)

也就是說任何人都可以編譯linux(只要你有能力的話)

這特性使得在linux嵌入式裝置市場中,取得幾乎是封殺的地位,android今天的位置就是這麼來的

windows在嵌入式裝置方面,似乎只有xbox而已

伺服器方面：

linux由於其安全性及效能利用方面佳,在市場地位有升高的趨勢

windows server有獨家架構(不要問我是啥架構),在市場也有一定的地位

安全性方面：

我為什麼要把這獨立出來講呢?原因很簡單嘛,一個不安全的東西,會有誰想去使用它呢?

linux因為有嚴格的權限控制受到需要高安全性的機器歡迎

另外目前多數的病毒多以windows為攻擊目標,linux暫時是安全的,linux甚至還有美國國家安全局開發的SElinux(一種安全性套件)

但是,嵌入式linux就不一樣了

用android當例子好了(我是說假如啦)

android藉由java去執行app

java是外掛程式的一種,既然是外掛程式,必然會有漏洞

而當發佈修補更新時,問題來了

嵌入式裝置的更新是交給廠商去執行的

而使用android作為手機系統的廠商又十分多

所以每當發現漏洞後,往往不能在數天內得到更新,最快也要等到數禮拜後才會有更新

且現在android平台上的釣魚程式可不少(病毒會往熱門的平台上發展)

所以並非所有的linux都是安全的

沒有office(word,powerpoint,excel等),不能教報告：

那你肯定沒有聽過openoffice和libreoffice這兩套開源的辦公軟體囉

同樣可以開.doc .docx .ppt .pptx .xls .xlsx

功能和介面也需有些不同,但它也可以做報告阿!誰說不可以的

話就講到這裡,我個人認為兩者各有利弊,我在寫這篇文章時,是用ubunut上的firefox寫的,(因為副系統windows中毒),這代表著windows能做到的事,在linux上也可以做到(我絕對沒有暗示你們linux比較不容易中毒) 至於linux和windows誰好呢?像信各位心中已經有底了 我非常歡迎各位在下方與我理性的討論 本文就到這裡,下次再見囉