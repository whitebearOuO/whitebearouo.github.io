---
layout: post
title: linux與windows的雙系統安裝
---

## 前言
其實之前有寫過一篇[windows和manjaro的雙系統安裝](https://whitebearouo.github.io/posts/windows%E5%92%8Cmanjaro%E7%9A%84%E9%9B%99%E7%B3%BB%E7%B5%B1%E5%AE%89%E8%A3%9D/)，但我後來改成用arch linux了，所以決定再來寫一篇。<br>
<br>
但這次是反過來，先安裝arch，再安裝windows。<br>
其實滿簡單的，就如同之前在[archlinux的安裝](https://whitebearouo.github.io/posts/archlinux%E7%9A%84%E5%AE%89%E8%A3%9D/)那篇的結尾提到，只要用gparted切一個空間就好。<br>
這麼說的話<br>
感覺會有點像gparted的教學耶......<br>
<br>
總之最大的重點，就是使用[grub](https://wiki.archlinuxcn.org/zh-tw/GRUB)，這樣就可以在按電源鍵後，進入選單選擇你要的系統。

## 安裝archlinux
總之你可以先來這一篇[archlinux的安裝](https://whitebearouo.github.io/posts/archlinux%E7%9A%84%E5%AE%89%E8%A3%9D/)，把arch裝好。

## 使用gparted切割分區
### 安裝
安裝[gparted](https://gparted.org/download.php)，至於如何安裝，需要看各位的linux是哪一個了。<br>
<br>
以我使用的arch為例：
```
sudo pacman -Syu gparted
```

ubuntu：
```
sudo apt-get install gparted
```
<br>
在官網上還有寫其他發行版的安裝方式，有Debian、Fedora、Mageia、OpenSUSE。<br>
如果上面沒有你使用的發行版的話，可能就得靠你自己去尋找其他安裝方式了。<br>
<br>
順帶一提，gparted有iso檔，所以你也可以把他做成開機碟。

### 使用方式
#### 簡單介紹畫面
![](/assets/img/image/linux與windows的雙系統安裝/gparted畫面.png)<br>
這是gparted的畫面，從這裡就可以看出來這顆硬碟被切了四個分區。<br>
最左邊的nvme0n1p1，是[efi分區](https://wiki.archlinuxcn.org/zh-tw/EFI_%E7%B3%BB%E7%BB%9F%E5%88%86%E5%8C%BA)。通常efi分區不用那大，我是用archinstall讓他自己跑的，預設就是1GB。<br>
第二個nvme0n1p2，是我的linux分區，你可以看到他的檔案系統是btrfs。<br>
第三個是windows自己跳出來的保留分區。<br>
最後一個便是windows系統的分區了。<br>
<br>
我選擇讓他們大概一人一半，因為我平常還是兩種都會使用，~~不然幹嘛搞雙系統~~。<br>
各位就自行斟酌要給他們多少空間吧，windows的系統會佔據的空間比arch多很多，不過到底是多多我也忘了（<br>

#### 切割
按下>>|就可以開始拉了。<br>
![](/assets/img/image/linux與windows的雙系統安裝/調整大小—移動已選的分割區.jpg)<br>
<br>
真的是用拉的，你想用多少就拉多少，好了之後按調整大小。<br>
![](/assets/img/image/linux與windows的雙系統安裝/調整大小.png)<br>
<br>
他會在底下顯示你要做的動作，弄好之後按下v就OK了。<br>
![](/assets/img/image/linux與windows的雙系統安裝/確認.png)<br>

## 安裝windows
去[microsoft官方](https://www.microsoft.com/zh-tw/software-download/windows10ISO)下載iso檔ㄅ<br>
![](/assets/img/image/linux與windows的雙系統安裝/下載windows.png)<br>
<br>
然後在安裝windows的時候，選我們剛剛切出來的新分區就好了。<br>
至於詳細安裝方式我有空再寫（

## 剩下的一些設定
通常以這個順序（arch->windows）安裝完之後，windows會變成你開機順位的第一個，所以我們要去BIOS裡面調一下。<br>
<br>

![](/assets/img/image/linux與windows的雙系統安裝/BIOS_boot.jpg)<br>
如果你就只有安裝windows跟arch，總共有三個可以選。<br>
<br>
GRUB會讓你到GRUB選單，讓你可以選要開哪一個系統，像底下這張圖一樣。<br>
![](/assets/img/image/linux與windows的雙系統安裝/grub畫面)<br>
那當然剛弄好的時候，就只會有黑底白字給你看，字還又細又小。<br>
可以搜尋grub theme，找一個你喜歡的。<br>
像是我ㄉ[Minecraft畫面](https://github.com/Lxtharia/minegrub-theme/tree/main)，每次開機被室友看到，他都以為我要玩電腦。<br>
<br>
Windows Boot Manager會讓你一開機就進windows。<br>
UEFI OS會直接進arch。<br>
<br>
把grub移到第一個就好。

## 結尾
我在想有沒有必要把每個步驟都寫得非常詳細，畢竟感覺會想裝雙系統的人應該早就知道怎麼裝系統了，~~而且我有點懶得再重新安裝一次拍照下來~~<br>
不過我剛剛發現我很久很久以前寫的教學圖片還活著，所以我決定搬運一下他們。<br>
<br>
那麼，教學差不多就到此結束了。<br>
因為這篇文真的拖了好久好久，裡面可能會有一些缺漏，如果有問題或是有其他建議，歡迎在底下留言告訴我。