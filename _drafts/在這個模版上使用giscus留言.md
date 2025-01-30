---
layout: post
title: 在這個模版上使用giscus留言
---

## 前言
這個主題是由cotes2020提供的chirpy。

## 教學
前往giscus的網站<https://giscus.app/zh-TW>。<br>
~~接下來的步驟其實直接看著giscus上面的教學做就好了（~~<br>

---

### 準備
使用giscus的repo要是公開的，不過大家都要寫網誌了，應該都是公開的了ㄅ。<br>
沒有的話，現在就去調一下。<br>
<br>
接著安裝[giscus](https://github.com/apps/giscus)，按下那個大大的install吧。<br>
![](/assets/img/image/在這個模版上使用giscus留言/giscus安裝.png)<br>
<br>
你可以選擇讓所有的repo安裝，或是只幫單一repo安裝。<br>
這邊我就只幫我的whitebearouo.github.io裝了。<br>
![](/assets/img/image/在這個模版上使用giscus留言/giscus安裝頁面.png)<br>
<br>
開啟repo的discussions功能。<br>
到repo頁面，點setting，在general下面打開。<br>
![](/assets/img/image/在這個模版上使用giscus留言/github_setting.png)<br>
<br>
![](/assets/img/image/在這個模版上使用giscus留言/discussions.png)<br>
<br>
按下start discussion就OK了。<br>
![](/assets/img/image/在這個模版上使用giscus留言/discussion頁面.png)<br>
<br>

### 繼續
上面的都準備好，把你的repo輸上去就能確認ㄌ。<br>
![](/assets/img/image/在這個模版上使用giscus留言/giscusOK.png)<br>
<br>
把`data-repo`、`data-repo-id`、`data-category`、`data-category-id`的東西，貼到`_config.yml`的giscus區就好。<br>
![](/assets/img/image/在這個模版上使用giscus留言/giscus複製貼上.png)

### 完成
這樣就可以留言ㄌ。<br>
![](/assets/img/image/在這個模版上使用giscus留言/留言畫面.png)<br>
<br>
會出現在repo的discussion上。<br>
![](/assets/img/image/在這個模版上使用giscus留言/discussion畫面.png)