---
layout: post
title: My New Post
date: 2024-09-26 22:20 +0800
categories: [test]
tags: [github, github.io, jekyll]
description: 測試網頁兼指令紀錄
---

## 指令
一直記不起來指令<br>
[jekyll-chirpy網站](https://chirpy.cotes.page/)

---

```
bundle exec jekyll s
```

[jekyll compose](https://github.com/jekyll/jekyll-compose)

new draft
```
bundle exec jekyll draft "My new draft"
```

rename
```
bundle exec jekyll rename _drafts/my-new-draft.md "My Renamed Draft"

```

public draft
```
bundle exec jekyll publish _drafts/my-new-draft.md
```

rename post
```
bundle exec jekyll rename _posts/2014-01-24-my-new-draft.md "My New Post"
```

刪除husky
```
npm uninstall husky && git config --unset core.hooksPath
```

```
rm -f .git/hooks/husky
```
