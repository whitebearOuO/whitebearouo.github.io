---
layout: post
title: windows和manjaro的雙系統安裝
date: 2024-09-29 16:35 +0800
categories: [教學, 系統安裝]
tags: [windows, linux, manjaro]
description: 在一個硬碟裡同時安裝windows和linux
---

這篇文章應該還會慢慢更新，剛接觸linux還會有很多不完善的地方。如果有什麼建議或可以改善的地方，還請各位幫忙留言指導了> <
以manjaro KDE為範例，系統安裝完之後會再介紹一些manjaro的設定。

## 系統安裝

### 安裝windows
我們先安裝windows，在安裝windows的過程中就預留空間給manjaro安裝。
首先先在要用來安裝系統的磁碟機，按新增，看你要給windows多大的空間就新增多少。
![P_20240423_221348](https://hackmd.io/_uploads/BkK6qDezA.jpg)

輸入你要的大小，單位是MB，自己拿計算機算一下吧。
![P_20240423_221416](https://hackmd.io/_uploads/By2DsPlzA.jpg)

確認。
![P_20240423_221425](https://hackmd.io/_uploads/ryN9oPlMR.jpg)

這時候你會發現多了三個磁碟分割，windows系統會安裝到剛剛切割的磁碟機0，類型是「主要」的那一個分區。按下一步。
![P_20240423_221431](https://hackmd.io/_uploads/B1E12vlMC.jpg)

熟悉的安裝windows的畫面。裝完windows就可以關掉換裝manjaro了。
![P_20240423_221512](https://hackmd.io/_uploads/Syt7mdxzC.jpg)

### 安裝manjaro
有裝manjaro iso檔的usb，插進電腦，改成開機碟。
進到設定畫面的時候記得要快點動，不然過太久的話他就會直接進到下一步了。
![upload_0e5d115c80184cd88768d78133486e39](https://hackmd.io/_uploads/SkvPHy770.jpg)

* tz=Asia/Taipei
* keytable=us
* Lang=zh_TW
把上面三個改成這樣之後，就可以選擇第四個Boot with open source drivers了。
![P_20240423_222503](https://hackmd.io/_uploads/SJV-VugMR.jpg)

按Launch installer。
![P_20240423_222623](https://hackmd.io/_uploads/r1wyrOxGC.jpg)

選好繁體中文，下一步。
建議安裝過程可以連網，他會直接幫你選擇好語言跟時區。
如果是在筆電上面安裝，記得插電。
![Screenshot_20240516_022539](https://hackmd.io/_uploads/H1gGU1m7R.png)

選擇時區。
![Screenshot_20240516_022619](https://hackmd.io/_uploads/HkqLUymXC.png)

鍵盤選擇English(US), Default就好了。
![Screenshot_20240516_022627](https://hackmd.io/_uploads/SytO817mA.png)

我們要同時安裝windows和manjaro，這時候我們選擇把兩個系統裝在同一個硬碟上。
可以看到底下顯示還有349.51GB灰色的剩餘空間，就是前面在安裝windows時切出來的未配置的空間。
選擇手動分割。
![Screenshot_20240516_022633](https://hackmd.io/_uploads/ByYKLJXXA.png)

點剩餘空間，按建立。
![Screenshot_20240516_022719](https://hackmd.io/_uploads/BJM0wJmXA.png)

建立一個分割區。
容量大小：300MiB
檔案系統：fat32
掛載點：/boot/efi
旗標：boot
![Screenshot_20240516_022832](https://hackmd.io/_uploads/H1HgdkQ7A.png)

點剩餘空間，再建立一個分區。
![Screenshot_20240516_022859](https://hackmd.io/_uploads/B1_su1mXC.png)

剩下的空間就直接全部用掉了。
掛載點：/
![Screenshot_20240516_022952](https://hackmd.io/_uploads/HJkkKk77C.png)

下一步。
![Screenshot_20240516_023015](https://hackmd.io/_uploads/rktzty77C.png)

設定你的名稱與密碼。
![Screenshot_20240516_023042](https://hackmd.io/_uploads/HyvQKy7mC.png)

看你要不要在這邊裝office。
那我們就先選No office Suite，等系統安裝好之後再自己裝就好。
![Screenshot_20240516_023049](https://hackmd.io/_uploads/BkJHYyX7R.png)

給你看剛剛的設定，OK就按安裝。
![Screenshot_20240516_023055](https://hackmd.io/_uploads/H10OtkXQA.png)

現在安裝。
![Screenshot_20240516_023100](https://hackmd.io/_uploads/ry0ctkXm0.png)

裝完之後重新開機就完成了。

## 系統設定
### 主路徑中文改英文

原教學：<https://segmentfault.com/a/1190000037454534>

建議一開始就先處理這個，因為資料夾裡面如果有東西的話就會有一個新的資料夾跟一個舊的。
首先開啟konsole輸入
```
sudo pacman -S xdg-user-dirs-gtk
```
![image](https://hackmd.io/_uploads/Sy4acvUWA.png)

裝好後輸入
```
export LANG=en_US
xdg-user-dirs-gtk-update
export LANG=zh_TW.UTF-8
```

接著就會問你要不要改，按Update Names
![image](https://hackmd.io/_uploads/HJQgjwLWR.png)

![image](https://hackmd.io/_uploads/ByG7iwIWR.png)

這時候到了dolphin就會發現，側欄沒辦法直接連過去，因為資料夾名稱改了。
![image](https://hackmd.io/_uploads/H1MBsvLZ0.png)

按右鍵之後編輯。
![image](https://hackmd.io/_uploads/B1CBoDLb0.png)

改成新的路徑就好。
![image](https://hackmd.io/_uploads/rkgwowLb0.png)

---

## 輸入法
### 安裝中文輸入法
原教學：<https://home.gamer.com.tw/artwork.php?sn=5303263>
安裝完鍵盤輸入框架之後，會再安裝[小麥注音](https://github.com/openvanilla/fcitx5-mcbopomofo)來用。

安裝fcitx5-chewing
![image](https://hackmd.io/_uploads/ryAL0kdbA.png)

套用。
![image](https://hackmd.io/_uploads/SJPKAJOZ0.png)

安裝fcitx5-configtool
![image](https://hackmd.io/_uploads/SJkaCyOb0.png)

安裝manjaro-asian-input-support-fcitx5
![image](https://hackmd.io/_uploads/rkhe1g_WA.png)

如果有你需要的輸入法，就把他勾起來，如果需要打注音的話就不用管這邊了。
![image](https://hackmd.io/_uploads/HkA-yedW0.png)

接下來會介紹小麥輸入法的安裝。

---

### 小麥注音輸入法
<https://github.com/openvanilla/fcitx5-mcbopomofo>
<https://github.com/openvanilla/fcitx5-mcbopomofo/wiki/%E5%A6%82%E4%BD%95%E5%9C%A8-Arch-Linux-%E4%B8%8A%E5%AE%89%E8%A3%9D-fcitx5-mcbopomofo>

在 git clone 本專案後，執行以下命令就好了。

```
# within the git working directory
cd distro/archlinux/
sudo pacman -Syy
makepkg -si
```

安裝完解壓縮，按右鍵就能在此處開啟終端機。
![image](https://hackmd.io/_uploads/By0fllOWC.png)

輸入上面的指令。
![image](https://hackmd.io/_uploads/Sk-cIxdWR.png)

我在別台電腦安裝的時候確實是使用上面的方法就完成了，不過在這台電腦的時候遇到一些問題。
一開始顯示的錯誤訊息是：

``
Could NOT find PkgConfig (missing: PKG_CONFIG_EXECUTABLE)
``

https://stackoverflow.com/questions/33380020/errorcould-not-find-pkgconfig-missing-pkg-config-executable
裡面的回答是This error is raised because the pkg-config utility is not available on your system.
只要在console裡面輸入以下指令就好。

```
sudo pacman -S pkg-config
```

但後面又出現了另一個錯誤訊息
``
Cmake was unable to find a build program corresponding to "Unix Makefiles". CMAKE_MAKE_PROGRAM is not set.
``

<https://blog.csdn.net/qq_29750461/article/details/125446311>
這裡是說有可能沒有安裝make，只要在console輸入以下指令就好

```
sudo pacman -S make
```

---

## 程式
### 如何下載yay
<https://github.com/Jguer/yay>

輸入以下指令就好。

```
sudo pacman -S --needed git base-devel yay
```

![image](https://hackmd.io/_uploads/r1LtVuuZ0.png)

---

### 切換獨顯內顯
#### 安裝

有envycontol跟optimus-manager可以用
這邊選擇使用envycontrol
<https://github.com/bayasdev/envycontrol>
<https://github.com/Askannz/optimus-manager>

在console輸入
```
yay -S envycontrol
```
輸入以下指令更改模式，分別為integrated、hybird、nvidia
```
sudo envycontrol -s <MODE>
```

#### GUI
在內建的安裝程式裡搜尋optimus gpu switcher就可以找到了
![image](https://hackmd.io/_uploads/H1yu79O-R.png)

![image](https://hackmd.io/_uploads/SkbhQ5ObR.png)

![image](https://hackmd.io/_uploads/ryRklcuWA.png)
記得切換完模式之後重新啟動。

### 安裝vscode
輸入指令至console。

```
yay -S visual-studio-code-bin
```
### 安裝Line
說真的我不是很喜歡用Line，但沒辦法，不管你有多討厭Line，終究還是會被逼著下載Line。
所以我們還是得來研究如何在linux上面下載Line，哈哈哈...嗚嗚...

原教學文章：<https://ivonblog.com/posts/linux-bottles-install-line/>

### 備份工具 timeshift
```
sudo pacman -S timeshift
```

介面淺顯易懂，基本上只要安裝完成打開就知道該怎麼做了。
timeshift沒辦法在網路硬碟或者是非linux的檔案系統（像是windows的ntfs3）備份，我有兩個硬碟，一個是拿來裝系統的，另一個原本是在用windows時，拿來裝遊戲的，所以他是windows的格式，我的備份檔只能跟系統放在一起，之後再想想還有什麼方法。

別人的教學文章：<https://ivonblog.com/posts/linux-timeshift-usage/>

## 其他問題

### grub頁面沒出現

後來又重新安裝了一次系統，然後也遇到了前面也遇過的問題。
安裝windows時，顯示「電腦所需的媒體驅動程式遺失」，這似乎是因為usb3.0驅動的關係，但我的筆電沒有2.0的孔，手邊也沒有2.0的usb，原本想只能等回家再處理。因為急著用筆電，所以先載了manjaro，硬碟預留了一些空間之後裝windows。
但後來想到可以載win11看看或是在pe系統用microsoft提供的安裝工具看看，後來是靠前者處理好了，win11不知道為什麼不會遇到驅動缺失。

直接在預留的空間安裝windows，也沒遇到安裝問題。但最後還是遇到了一個問題，windows可以開，manjaro可以開，但他們都是各自打開，要在BIOS把要開的調成開機順位的第一個。

結果只需要更新grub menu就好了。
```
sudo nano /etc/default/grub
sudo update-grub
```

參考資料：<https://forum.manjaro.org/t/grub-menu-not-showing-on-boot-boots-into-default-kernel-instead/13410/3>


## 延伸資料

## MSR、ESP與EFI分區是什麼
<https://baiyunju.cc/8773>

## manjaro的各種分區是什麼
<https://zhuanlan.zhihu.com/p/268508247>

* /boot/efi：FAT32，512M，启动分区
* /：ext4，10G，根分区，不需要太大
* /home：ext4，120G，用户分区，建议尽可能大，因为很多软件都默认把配置文件放在用户目录下
* /usr：ext4，100G，这个不是user的缩写，是用于存放程序以及数据的地方，涵盖了二进制文件，各种文档，各种头文件，还有各种库文件
* /var：ext4，50G，包含缓存、一些临时文件以及日志文件
* /srv：ext4，5G，用于存储本机或本服务器提供服务的数据，主要用于配置服务器，个人使用的话5G足够
* /opt：ext4，10G，一些第三方软件，
* swap：16G，交换分区

我現在還不太確定不自己預先設定會怎樣，我只有先設定啟動分區，再來就是根目錄了。
這裡面提到的其他資料夾都在我的根目錄之下

<https://hustlei.github.io/2018/11/msys2-pacman.html>
