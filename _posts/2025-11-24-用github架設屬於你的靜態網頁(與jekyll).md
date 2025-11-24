---
layout: post
title: 用github架設屬於你的靜態網頁(與jekyll)
date: 2025-11-24 11:45 +0800
categories: [教學, 網站]
tags: [github page, jekyll, chirpy]
description: 我有拖拖病
---

## 前言
有一天弟弟看到有人在賣線上課程，在教如何用github架設靜態網站。<br>
他傳給我，跟我說我怎麼沒有寫教學。<br>
我才想到，對耶！<br>
<br>
沒想到寫了那麼多東西(其實也大概20出頭而已)，卻沒有寫過如何用github架靜態網頁。<br>
明明我的blog也是用github跟jekyll架設的，所有的過程也都自己嘗試過。<br>
<br>
總之事不宜遲，現在就來介紹吧。

## 一些簡單的小介紹
要利用github來架靜態網站其實不難。<br>
開一個repo -> 在裡面放一個index.html -> 到設定打開就好了<br>
![](/assets/img/image/用github架設屬於你的靜態網頁(與jekyll)/github_setting.png)<br>
<br>
欸就這嗎？對啊就這，真的。

---

我剛剛寫了一個超簡略的html，請看下方圖片。<br>
我把它放在我的repo的根目錄。<br>
![](/assets/img/image/用github架設屬於你的靜態網頁(與jekyll)/html範例.png)<br>
<br>
然後到剛剛設定那邊，選擇你要用的分支，他就會自己跑了。<br>
他上面有一個小提醒，因為我的repo是私人的，但page還是公開的。<br>
![](/assets/img/image/用github架設屬於你的靜態網頁(與jekyll)/簡略的完成.png)<br>
<br>
<https://whitebearouo.github.io/psychic-fortnight/><br>
這樣子網站就出來了，可以點上面的連結看看，連結的樣子會是`https://你的使用者名稱.github.io/你的repo名稱`<br>

## 如何讓網站變得更好看
可以自己寫css還有套點模板之類ㄉ，那剛剛的圖片裡也有出現一個東西，就是標題提到的jekyll。<br>
你可以直接去看[github給的文檔](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll)。我使用的模板，也有提供[使用教學](https://chirpy.cotes.page/)。<br>
<br>
那我使用的模板是[cotes2020](https://github.com/cotes2020)做的[chirpy](https://chirpy.cotes.page/)，所以等等也會以這個為例來進行介紹。

## chirpy on github

有兩個選項，一個是使用starter，一個是fork主題出來。<br>
使用starter的話比較簡單，如果只是想要單純寫寫文的話就可以選擇starter，作者本人推薦這一個選項。<br>
另一個fork主題出來，比較推薦想要修改功能，還有更改UI介面之類的人。但在升級的時候會比較困難一些，所以建議有這些需求，還有對jekyll比較熟習的人再選這個選項。<br>
<br>

## 創建repo的方式
### 使用starter
1. 登入github，然後到[starter](https://github.com/cotes2020/chirpy-starter)那邊。
2. 點<kbd>Use this template</kbd>，然後點<kbd>Create a new repository</kbd>。
3. 把repo的名稱取為`<你的使用者名稱>.github.io`，你的使用者名稱請填入你自己的github使用者名稱，並且要用小寫。

### fork repo
1. 登入github
2. [fork repo](https://github.com/cotes2020/jekyll-theme-chirpy/fork)
3. 把repo的名稱取為`<你的使用者名稱>.github.io`，你的使用者名稱請填入你自己的github使用者名稱，並且要用小寫。

## 設置環境
### 使用開發容器
用開發容器，就可以避免把一堆依賴混在一起，讓你的電腦裡面變得亂七八糟。<br>
1. 安裝docker
    - Windows/MacOS，安裝[Docker Desktop](https://www.docker.com/products/docker-desktop/)
    - Linux，安裝[Docker Engine](https://docs.docker.com/engine/install/)
2. 安裝[Vscode](https://code.visualstudio.com/)和[Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
3. 複製repo下來
    - Docker Desktop：啟動vscode，把[儲存庫複製到容器磁碟區](https://code.visualstudio.com/docs/devcontainers/containers#_quick-start-open-a-git-repository-or-github-pr-in-an-isolated-container-volume)。
    - Docker Engine：把檔案複製到本機，[透過vscode在容器中開啟](https://code.visualstudio.com/docs/devcontainers/containers#_quick-start-open-an-existing-folder-in-a-container)。

雖然也可以直接在本機設定環境，但之前用的時候會有種真的是下載了一堆有的沒的到電腦裡的感覺，然後依賴又衝突來衝突去的。<br>
所以我還是比較推薦使用開發容器，如果你想直接在本機設定環境，可以去看作者的教學。

## 用法
### 啟動jekyll伺服器
```
bundle exec jekyll serve
```
過一下下就可以在<http://127.0.0.1:4000>存取了。

### 配置
到`_config.yml`更改。<br>
裡面都有詳細的註釋，進去看就知道要怎麼改了。

### 社交聯絡方式
在`_data/contact.yml`可以設置你的聯絡方式。<br>
他會顯示在網頁側欄底部。<br>
![](/assets/img/image/用github架設屬於你的靜態網頁(與jekyll)/網頁側欄聯絡方式.png)<br>
如果有不想要的，就把它註解掉，想要的就取消註解。

### 部屬
到`config.yml`確定你的url設定正確，然後就跟最一開始說的一樣，弄github page就好了。
不過這次在page那邊的Bulid and Deployment的Source要選Github Actions，之後只要推送任何東西，就會自動觸發Actions工作流程，建置完後網站就會自動部屬了。<br>
![](/assets/img/image/用github架設屬於你的靜態網頁(與jekyll)/github_actions.png)

## 結束
大概就醬。<br>
忘記多久以前開了這個草稿，結果丟到現在才補完。<br>
想不太起來一開始想怎麼寫，變得有點像在翻譯作者的教學:P