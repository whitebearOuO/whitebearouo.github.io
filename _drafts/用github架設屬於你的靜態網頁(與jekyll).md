---
layout: post
title: 用github架設屬於你的靜態網頁(與jekyll)
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

---

有兩個選項，一個是使用starter，一個是fork主題出來。<br>
使用starter的話比較簡單，如果只是想要單純寫寫文的話就可以選擇starter，作者本人推薦這一個選項。<br>
另一個fork主題出來，比較推薦想要修改功能，還有更改UI介面之類的人。但在升級的時候會比較困難一些，所以建議有這些需求，還有對jekyll比較熟習的人再選這個選項。<br>
<br>

### 使用starter
1. 登入github，然後到[starter](https://github.com/cotes2020/chirpy-starter)那邊。
2. 點<kbd>Use this template</kbd>，然後點<kbd>Create a new repository</kbd>。
3. 把repo的名稱取為`<你的使用者名稱>.github.io`，你的使用者名稱請填入你自己的github使用者名稱，並且要用小寫。

### fork repo
1. 登入github
2. [fork repo](https://github.com/cotes2020/jekyll-theme-chirpy/fork)
3. 把repo的名稱取為`<你的使用者名稱>.github.io`，你的使用者名稱請填入你自己的github使用者名稱，並且要用小寫。