---
layout: post
title: linux與windows的雙系統安裝
---

## 前言
其實之前有寫過一篇[windows和manjaro的雙系統安裝](https://whitebearouo.github.io/posts/windows%E5%92%8Cmanjaro%E7%9A%84%E9%9B%99%E7%B3%BB%E7%B5%B1%E5%AE%89%E8%A3%9D/)，但我後來改成用arch linux了，所以決定再來寫一篇。<br>
<br>
但這次是反過來，先安裝arch，再安裝windows。<br>
其實滿簡單的，就如同之前在[archlinux的安裝](https://whitebearouo.github.io/posts/archlinux%E7%9A%84%E5%AE%89%E8%A3%9D/)那篇的結尾提到，只要用gparted切一個空間就好。<br>
這麼說的話
感覺會有點像gparted的教學耶......

## 安裝archlinux
總之你可以先來這一篇[archlinux的安裝](https://whitebearouo.github.io/posts/archlinux%E7%9A%84%E5%AE%89%E8%A3%9D/)，把arch裝好。

## 使用gparted
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
![](/assets/img/image/linux與windows的雙系統安裝/gparted畫面.png)<br>
這是gparted的畫面，從這裡就可以看出來這顆硬碟被切了四個分區。<br>
最左邊的nvme0n1p1，是[efi分區](https://wiki.archlinuxcn.org/zh-tw/EFI_%E7%B3%BB%E7%BB%9F%E5%88%86%E5%8C%BA)。通常efi分區不用那大，我是用archinstall讓他自己跑的，預設就是1GB。<br>
第二個nvme0n1p2，是我的linux分區，你可以看到他的檔案系統是btrfs。<br>
第三個是windows自己跳出來的保留分區