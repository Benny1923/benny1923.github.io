---
title: windows 10 沙盒 正式上線 自定義配置檔 自己寫
tags:
  - sandbox
  - windows
  - windows 1903
  - 沙盒
id: '479'
categories:
  - - Windows
date: 2019-05-25 12:45:53
redirect_from:
  - 
---

這星期1903上線拉，最讓我期待的是windows 10終於有內建的沙盒程式啦。

啟用方法很簡單，先確認自己更新到1903，然後去舊版控制台，程式集裡的「開啟或關閉Windows功能」把「Windows 沙箱」選項打勾然後確定完重新開機，然後你就可以在你的開始列表中找到「Windows Sandbox」。  
點下去就有一個隨開即用的沙盒模式，直接關掉裡面發生的事情就當沒有發生過，重開又是一個乾淨的新系統。

以上就是沙盒的介紹，那Windows 沙盒也提供自定義配置檔案來對沙盒做部分修改，比如說讓沙盒存取外部檔案之類的。

首先先建立一個空檔案吧副檔名叫 **.wsb**

然後用記事本或其他文字編輯器打開它  
輸入以下的文字

 <configuration> 設定放這 </configuration>

所以這是一個xml格式的設定檔  
所以可以在 `configuration` 的區段下寫配置  
目前我查到支援的配置有

**虛擬GPU(VGU)**  

```xml
<vgpu>參數</vgpu>
```

有 `Disable` 和 `Default` 兩個參數  

**網路功能**(Networking)  

```xml
<networking>參數</networking>
```

有 `Disable` 和 `Default` 兩個參數  

**資料夾映射**(MappedFolders)  

```xml
<mappedFolders> 子項目 </mappedFolders>
```

這裡面有子項目，參見下一節說明  

**資料夾映射子項**  

```xml
<mappedFolder>
    <hostFolder>外部主機路徑</hostFolder> 
    <readOnly>參數</readOnly> 
</mappedFolder>
```

`HostFolder` 參數：外部主機資料夾路徑，例如：`C:\Users\Public\Downloads`  
`ReadOnly`     參數：是否為唯讀模式，接受 `true` 或 `false`  
備註:目前所有的映射都是指向桌面，希望未來可以有指向其他地方的設定  

**登入時執行**(LogonCommand)  

```xml
<logonCommand> <command>執行的指令</command> </logonCommand>
```

`Command` 參數：指令，程式或某個批次檔，例如要打開C:\\的話：`explorer.exe C:\`  

所以比如說我想把我的下載資料夾映射到沙盒中  
設定檔就會長這樣  
config.wsb

```xml
<configuration> 
<mappedFolders> 
    <mappedFolder>
        <hostFolder>E:\\Downloads</hostFolder> 
        <readOnly>true</readOnly> 
    </mappedFolder> 
</mappedFolders> 
</configuration>
```

最後直接點開你寫好的檔案，你就得到一個桌面上有一個映射資料夾的臨時windows環境了  

這就是全部拉，需要參考的可以去下面參考連結找，有提供兩組範例  
上一次寫文章都隔了423天，真的好久，預名都續費1次了...

參考資料：微軟技術社群 [https://techcommunity.microsoft.com/t5/Windows-Kernel-Internals/Windows-Sandbox-Config-Files/ba-p/354902](https://bit.ly/2UmI3N7)