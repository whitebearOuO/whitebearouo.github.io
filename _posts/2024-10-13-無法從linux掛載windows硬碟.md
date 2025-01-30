---
layout: post
title: 無法從linux掛載windows硬碟
date: 2024-10-13 22:19 +0800
categories: [教學, linux]
tags: [archlinux, windows, NTFS, dirty, mount]
description: 我的linux又有問題了，是啊，到底是為什麼呢
---
---
## 我的系統
我用的是archlinux搭配KDE桌面，在同一顆硬碟裡面同時安裝了windows11。<br>
要掛載硬碟不難，只要點開dolphin，點側欄想掛載的硬碟就好。如果是windows的NTFS格式的硬碟，需要安裝[`NTFS-3G`](https://wiki.archlinux.org/title/NTFS-3G)，在掛載時需要輸入密碼。<br>
不過某天突然掛載不了了，顯示的錯誤訊息大概是：<br>
```
wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.
```
~~不過在使用的當下因為沒什麼心情debug，就直接把檔案丟到其他掛載得了的硬碟。~~ <br>
~~用完就當作沒事，後來才開始找處理方式。~~

## 處理方式
總之我先從StackExchange上面找到[這篇文](https://unix.stackexchange.com/questions/315063/mount-wrong-fs-type-bad-option-bad-superblock)<br>
前面提供的方式會把磁碟內容清掉，但我不可能清掉，畢竟他是我的windows耶，所以我參考了其他答案。<br>
<br>
1. 首先先用`lsblk`查看硬碟。
![](assets/img/image/無法從linux掛載windows硬碟/5.png)<br>
我是以分區的大小來判斷哪個是我的windows硬碟。
2. 如果看得到那顆硬碟，用`fdisk -l`看看系統有沒有辦法用他。
![](assets/img/image/無法從linux掛載windows硬碟/6.png)<br>
在這邊就可以看到最右邊有寫類型，寫著Microsoft，很清楚能知道這是我的windows了。
3. 再來輸入`fsck /dev/sda1`修理損壞的區域（/dev/sda1改成你自己的硬碟）<br>
有些人到這邊就結束了，很可惜不是我:( <br>
我在第三步遇到問題，之後又去查了其他方法。<br>

_是說後來才知道，這是給linux的指令，不知道這樣對NTFS格式的硬碟有沒有用......_

<br>
於是我來到了reddit的[這篇文章](https://www.reddit.com/r/archlinux/comments/17yc6yw/cant_mount_windows_partition)，裡面的回答帶著我到了[archlinux的維基](https://wiki.archlinuxcn.org/wiki/NTFS#%E6%97%A0%E6%B3%95%E7%94%A8_ntfs3_%E6%8C%82%E8%BD%BD%E8%A2%AB%E6%A0%87%E8%AE%B0%E4%B8%BA%E8%84%8F%E7%9A%84%E5%88%86%E5%8C%BA)<br>
請讓我直接把維基頁面截過來這邊吧。<br>
![](assets/img/image/無法從linux掛載windows硬碟/2.png)<br>
使用`dmesg`會幫你判斷這個情況，好巧不巧他回得真的跟上面說得一模一樣耶。<br>
```
sdb1: volume is dirty and "force" flag is not set!
```
然後就用了[`ntfsfix`](https://man.archlinux.org/man/ntfsfix.8)的`--clear-dirty`。<br>
使用方式是`ntfsfix /dev/sda1 --clear-dirty`（/dev/sda1改成你自己的硬碟，請參考以下圖片）<br>
![](assets/img/image/無法從linux掛載windows硬碟/1.png)<br>
問題就這麼解決了，真是開心:D（記得指令用不了的話就加上sudo）

## 所以我說那個dirty硬碟是怎麼一回事
看到的時候我也很疑惑，髒的硬碟到底是什麼？<br>
StackExchange的[這篇文章](https://unix.stackexchange.com/questions/748468/why-is-ntfs-has-a-dirty-mark-and-why-cant-ntfs3-mount-dirty-ntfs-partitions)底下的回答說，這代表這個分區的metadata不一致，如果在讀寫模式使用他，可能會造成資料遺失。<br>
通常會在windows裡用`chkdsk`來處理，用`ntfsfix`不會處理不一致的問題，只是把髒的標誌刪除。<br>

## 在windows執行chkdsk
我直接以管理員身份執行cmd，輸入`chkdsk`。<br>
![](assets/img/image/無法從linux掛載windows硬碟/3.png)<br>
在階段三發現問題，要輸入`chkdsk -scan`，我在想可能是因為最前面寫到的，沒有指定-F參數，所以正在以唯讀模式執行chkdsk。<br>
![](assets/img/image/無法從linux掛載windows硬碟/4.png)<br>
跑完之後，他說沒有找到問題，不需要進一步的動作，所以這樣應該就OK了。

## 參考文章
- [Why is NTFS has a dirty mark and why can't NTFS3 mount dirty NTFS partitions?](https://unix.stackexchange.com/questions/748468/why-is-ntfs-has-a-dirty-mark-and-why-cant-ntfs3-mount-dirty-ntfs-partitions)
- [archlinux NTFS](https://wiki.archlinuxcn.org/wiki/NTFS)
- [archlinux NTFS-3G](https://wiki.archlinux.org/title/NTFS-3G)
- [mount: wrong fs type, bad option, bad superblock](https://unix.stackexchange.com/questions/315063/mount-wrong-fs-type-bad-option-bad-superblock)
- [Why is NTFS has a dirty mark and why can't NTFS3 mount dirty NTFS partitions?](https://unix.stackexchange.com/questions/748468/why-is-ntfs-has-a-dirty-mark-and-why-cant-ntfs3-mount-dirty-ntfs-partitions)
