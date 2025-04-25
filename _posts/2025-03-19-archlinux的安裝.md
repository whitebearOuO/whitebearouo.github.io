---
layout: post
title: archlinux的安裝
date: 2025-03-19 15:09 +0800
categories: [教學, linux]
tags: [arch, linux, os, 系統]
description: ようこそ、archlinuxの世界へ......
---

## 前言
我第一次用的是manjaro，再來用EndeavourOS，最後想說：「那我幹嘛不要用原版arch linux就好了？」<br>
就這樣，我又踏上了新的旅程，開始安裝arch linux。<br>
沒想到我就算看著人家的教學做不出來，但也找不到問題在哪，最後還是直接使用了arch linux的安裝腳本。<br>
<br>
所以此篇文章是以arch linux安裝腳本為範例。

## 內文
雖然查資料的時候，但到大家的介紹說建議一開始不要直接用腳本，要一步一步認識。<br>
但我覺得對於新手來說，使用腳本也不錯吧，至少可以先嘗試使用arch了。<br>

### arch的iso檔
前往arch的官網<https://archlinux.org/download/>下載iso檔。<br>
在這裡面有各個國家提供的載點，在台灣就直接選台灣節點吧！你可以選擇到官網找你喜歡的載點，或是直接在這邊點連結<https://archlinux.org/download/>。<br>
<br>
![](/assets/img/image/archlinux的安裝/archlinuxtw.png)<br>
沒有特別的需求的話，選紅色框框內的就好了。<br>
如果想下載舊版的，可以點最上面的`..`，就可以到上一個目錄去尋找舊版本的。<br>
<br>
獲得iso檔之後，可以使用ventoy或rufus等工具製作開機USB。<br>
有需要的話可以參考這篇[ventoy使用教學](https://whitebearouo.github.io/posts/ventoy%E4%BD%BF%E7%94%A8%E6%95%99%E5%AD%B8/)。<br>

### 開始安裝
到BIOS把USB的開機順位調到第一之後，選擇你的arch iso。<br>
<br>
在後面你可能會遇到安裝package時報錯，可以考慮先使用`pacman -Sy archlinux-keyring`，避免後面遇到又要重新用一次。可以參考[安裝package報錯](#安裝package報錯)。<br>
<br>
接著輸入`archinstall`即可使用安裝腳本。<br>
把archinstall調成中文可能會遇到字體缺失，所以建議使用英文。<br>
基本上照自己的需求選擇，腳本內都寫的滿清楚的。<br>
<br>
圖片上寫的字有點小，~~看不到就算ㄌ~~。<br>
需要注意的下面有再打字提到，所以問題應該不大。<br>
我這個archinstall的畫面是202409的iso，後來發現202503的iso有改過，可以自己去看看。<br>
![](/assets/img/image/archlinux的安裝/archinstall選單.jpg)<br>
<br>
需要注意的內容：<br>
1. 安裝桌面
2. 設定使用者帳號
3. 預先安裝package（noto-fonts-cjk）

第一點：<br>
如果沒有安裝桌面的話，archlinux安裝好之後你就只會有終端機畫面，沒有圖形化桌面可以用ㄌ。<br>
桌面有許多類型可以選擇，我選擇的是KDE桌面。<br>
![](/assets/img/image/archlinux的安裝/選擇桌面.jpg)<br>
<br>
第二點：<br>
如果沒有設定使用者帳號，只有root帳號的話，在安裝好之後就會發現沒有使用者可以選。<br>
![](/assets/img/image/archlinux的安裝/沒有使用者.jpg)<br>
<br>
真的很可憐......<br>
此時你只能選擇進入tty裡面用指令新增使用者，或是重新安裝了。<br>
<br>
第三點：<br>
這點其實問題不大，就算全部安裝好之後再安裝也沒關係。<br>
只是一開始進去的時候會發現一堆字都變成白色方塊，要在terminal裡面打`sudo pacman -S noto-fonts-cjk`。<br>

---

![](/assets/img/image/archlinux的安裝/確認.jpg)<br>
<br>
設定完之後按install，會顯示你剛剛選的配置，確定OK就繼續吧。<br>
<br>
如果沒有要幹嘛可以按esc跳過就好。<br>
![](/assets/img/image/archlinux的安裝/chroot嗎.jpg)<br>
<br>
安裝完畢後即可輸入reboot，開始享受你的archlinux :D<br>
![](/assets/img/image/archlinux的安裝/安裝完畢.jpg)<br>
<br>
輸入密碼登入吧。<br>
![](/assets/img/image/archlinux的安裝/登入畫面.jpg)

### 可能遇到的問題
#### 安裝package報錯
你可能會在安裝package時遇到一串紅字。<br>
```
error: libpgn: signature fron "Balló György (bgyorgy@archlinux.org)" is unknown trust :: File /ant/var/cache/pacnan/pkg/libpgn-5.3.128-3-x86_64.pkg.tar.zst is corrupted (invalid or corrupted package (PGP signature)).
```
之類的，可以參考底下照片。<br>
![](/assets/img/image/archlinux的安裝/安裝package錯誤.jpg)<br>
<br>
在reddit的[這篇文章](https://www.reddit.com/r/archlinux/comments/1htbi9z/error_failed_to_install_packages_to_new_root/)裡boomboomsubban提到，只要輸入`pacman -Sy archlinux-keyring`更新keyring就好了。

#### 安裝雙系統但時間不同步
參考Abhishek Prakash的[文章](https://itsfoss.com/wrong-time-dual-boot/)。<br>
```
sudo timedatectl set-local-rtc 1
```

### 一些建議你裝的東西
arch有pacman可以幫你裝東西，不過還是可以用其他工具，像是[yay](https://github.com/Jguer/yay)或是[git](https://git-scm.com/)。<br>
我還沒寫過安裝教學，但你可以考慮去他們官網看看怎麼安裝就好ㄌ。

#### bauh
bauh是用來管理程式（application）跟套件（package）的工具。<br>
可以先裝好他，再用他去裝其他東西。<br>
安裝方式請參考[這篇文章](https://whitebearouo.github.io/posts/bauh-%E5%9C%A8linux%E4%B8%AD%E7%AE%A1%E7%90%86%E7%A8%8B%E5%BC%8F%E7%9A%84%E5%B7%A5%E5%85%B7/)。

#### TLP
一個基本上裝了之後就可以放著不管他的工具。可以幫助你省電。<br>
想看詳細內容請前往arch官方看[文檔](https://wiki.archlinuxcn.org/wiki/TLP)，我懶懶就不介紹ㄌ。<br>
```
sudo pacman -S tlp
```
還有tlpui可以讓你不用用命令行改東西，可以用GUI介面，安裝方法跟上面一樣只要把tlp改成tlpui就好。<br>
![](/assets/img/image/other_pic/好有感覺謝謝.jpg)

#### 藍芽
你可以來[這邊](https://wiki.archlinuxcn.org/zh-tw/%E8%93%9D%E7%89%99)看arch官方的介紹。<br>
我個人需要的是安裝`bluetoothctl`然後啟用藍芽服務就好ㄌ。<br>
<br>
安裝`bluetoothectl`：<br>
```
sudo pacman -S bluetoothctl
```
開啟藍芽服務：<br>
```
sudo systemctl start bluetooth
```
讓他在開機時自動啟動：<br>
```
sudo systemctl enable bluetooth
```

#### 防火牆
```
sudo pacman -S firewalld
```
裝好後開啟就好。

#### grub
選個你喜歡的吧，我找了一個Minecraftㄉ你想用的話可以去看看<https://github.com/Lxtharia/minegrub-theme/tree/main>。<br>
![](/assets/img/image/mygo/我喜歡企鵝.jpeg)

## 結尾
大概就是醬。<br>
啊我是裝雙系統arch+windows，至於如何裝雙系統，又是另一件事了（遠目<br>
其實你只要留一個空間給window裝進去就好ㄌ。<br>
<br>
偷偷說我是用gparted在linux切出一個空間就可以裝windows進去了。