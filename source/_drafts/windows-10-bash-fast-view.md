---
title: Windows 10 linux功能不專業快速導覽
tags:
  - apt-get
  - bash
  - Ubuntu
  - windows
  - windows 10
  - windows love linux
id: '394'
categories:
  - - Windows
date: 2016-08-05 23:05:49
---

Windows 10 一歲啦!! 微軟官方在數天前向廣大的用戶推送大更新 在眾多更新的功能中，令我最期待的當然是... (碎鼓聲響起) Windows 10 內建bash拉!! 是原生的bash喔! 那就讓我快速導覽一下這功能有甚麼吧 等等...我是不是忘記說開啟這功能的方法 關於這點 這裡已經有人寫好了教學了，非常清楚喔(原本我也想寫，但晚了一天，被別人搶先一步了) [http://blog.kkbruce.net/2016/08/howto-enable-windows10-1607-ubuntu-bash.html](http://blog.kkbruce.net/2016/08/howto-enable-windows10-1607-ubuntu-bash.html) 那我們開始吧 首先，第一次啟動該功能後 會詢問你是否同意該條款(反正就輸入Y再按ENTER就對了) 接下來會下載及安裝一些初始化套件 完成後初始化後進入安裝階段 你只需要回答兩個問題就好 1."新"使用者名稱: 不是root，不必和windows使用者相同，如下圖所示 2."新"使用者密碼: 在座各位都有下過passwd指令吧，輸入兩次相同密碼即可 [![windows10bash](https://blog.bennyling.cc/wp-content/uploads/2016/08/windows10.jpg)](https://blog.bennyling.cc/wp-content/uploads/2016/08/windows10.jpg) 更新方式 管理套件方式同ubuntu採用apt-get指令來執行，新使用者沒有root權限，所以必須在apt-get指令前面加上sudo [![windows10](https://blog.bennyling.cc/wp-content/uploads/2016/08/windows10-1.jpg)](https://blog.bennyling.cc/wp-content/uploads/2016/08/windows10-1.jpg) [![working](https://blog.bennyling.cc/wp-content/uploads/2016/08/working.png)](https://blog.bennyling.cc/wp-content/uploads/2016/08/working.png) 他支援甚麼? 支援的可多著呢! ssh、openssl、nano、vi等等(懶得打，反正很多就對了(X 常見的指令都見的到 沒有?? sudo apt-get install \[指令名稱\] 試試看 總而言之 windows love linux不是隨便說說的 不專業導覽到這，我好像甚麼也沒講(是的，什麼也沒說 這篇文有結論嗎?(謎之聲:好像沒有。有了!「廢文一篇」