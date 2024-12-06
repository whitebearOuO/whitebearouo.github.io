---
layout: post
title: bauh-在linux中管理程式的工具
date: 2024-12-02 16:36 +0800
categories: [linux, 程式]
tags: [bauh, linux, arch linux, ubuntu, fpakman]
description: 用來管理程式（application）跟套件（package）的工具
---

## 前言
### bauh是什麼
bauh的github連結：<https://github.com/vinifmor/bauh><br>
<br>
如標題所言，bauh是用來管理程式（application）跟套件（package）的工具。前身是fpakman。<br>
目前支援格式：AppImage、Debian和Arch Linux軟體包（包括 AUR）、Flatpak、Snap和Web應用程式。<br>
bauh可以連動timeshift，在更新東西之前，可以幫你備份。

---

在我的安裝archlinux的文章裡（ 不知道會是這篇寫完還是那篇先寫完......<br>
提到我第一次用的是manjaro，再來用EndeavourOS。<br>
manjaro有個好處是他預載一個像應用程式商店的程式，只要打開，就能馬上安裝程式。<br>
<br>
新手可能不熟cmd，或者是有人就是愛GUI介面，這個工具就很方便。<br>
但是他有些時候會壞掉（我還沒找到原因），或是程式更新很慢（有時候會因為這樣讓我開不了discord）<br>
後來發現bauh，就改用他了。

### 安裝方式
#### 基於Arch的發行版
##### 安裝
使用[yay](https://github.com/Jguer/yay)下載。
```
yay -S bauh
```
<br>

使用[git](https://git-scm.com/)下載。
```
git clone  https://aur.archlinux.org/bauh.git
cd bauh
makepkg -si
```

---

可選性依賴：
- `timeshift`：系統備份
- `aria2`：多執行續下載
- `axel`：多執行續下載替代方案
- `libappindicator-gtk2`：tray-mode（GTK2桌面環境）
- `libappindicator-gtk3`：tray-mode（GTK3桌面環境）
- `xdg-utils`：在瀏覽器中開啟URL(xdg-open)
- `sqlite`, `fuse2`, `fuse3`：支援AppImage
- `flatpak`：支援Flatpaks
- `snapd`：支援Snaps
- `pacman`：ArchLinux套件管理支援
- `python3-lxml`, `python3-beautifulsoup4`：支援Web apps
- `python3-venv`：[隔離安裝](https://github.com/vinifmor/bauh#inst_iso)

##### 刪除
```
bauh --reset  #從HOME移除快取還有設定檔案
pacman -R bauh
```

#### 基於Ubuntu 20.04的發行版
##### 安裝
安裝依賴。
```
sudo apt-get install python3 python3-pip python3-yaml python3-dateutil python3-pyqt5 python3-packaging python3-requests
```
<br>
安裝bauh。
```
sudo pip3 install bauh
```

---

可選性依賴：（用apt-get或apt安裝）
- `aptitude`：Debian套件管理
- `timeshift`：系統備份
- `aria2`：多執行續下載
- `axel`：多執行續下載替代方案
- `libappindicator3-1`：tray-mode
- `sqlite3`, `fuse`：支援AppImage
- `flatpak`：支援Flatpaks
- `snapd`：支援Snaps
- `python3-lxml`, `python3-bs4`：支援Web apps
- `python3-venv`：[隔離安裝](https://github.com/vinifmor/bauh#inst_iso)
- `xdg-utils`：在瀏覽器中開啟URL(xdg-open)

##### 更新
方法一：
```
sudo pip3 install bauh --upgrade
```

方法二：
```
sudo pip3 uninstall bauh
sudo pip3 install bauh
```

##### 刪除
```
bauh --reset  #從HOME移除快取還有設定檔案
sudo pip3 uninstall bauh

```

### 使用
其實功能簡單易懂，大概是點進去你看得懂英文就會用了。<br>
<br>
先去開啟支援，記得在那之前先把你需要的支援下載好。<br>
按下bauh右下角的小螺絲。<br>
![](assets/img/image/bauh-在linux中管理程式的工具/開啟支援1.png)<br>
<br>
把你需要的勾起來就OK了。<br>
![](assets/img/image/bauh-在linux中管理程式的工具/開啟支援2.png)<br>

#### 日常使用範例
每次開機第一次開啟bauh的時候，他會先初始化。<br>
![](assets/img/image/bauh-在linux中管理程式的工具/1.png)<br>
<br>
搜尋你要的程式，按下install。<br>
如果要刪除就按uninstall。<br>
![](assets/img/image/bauh-在linux中管理程式的工具/使用範例1.png)<br>
<br>
你安裝的程式需要依賴，他也會直接跟你說。<br>
![](assets/img/image/bauh-在linux中管理程式的工具/依賴.png)<br>

## 結語
更多詳細的使用方式，可以直接去github上讀他的readme。<br>
<https://github.com/vinifmor/bauh>