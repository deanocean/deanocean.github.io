---
title: 這個版面如何實現? 01 - 讓影片可以響應式等比縮放
toc: true
disqusId: css-problem-01
date: 2022-09-06 02:10:36
categories:
  - 前端
tags:
  - CSS
  - 切版
# cover:
# thumbnail:
# excerpt:
---


## 前言

使用 iframe 影片，不只是寬度隨著螢幕縮放，高度也希望等比縮放時，該怎麼做?

解法是：
iframe 外面包一層容器，外面的容器設定 `padding-top` 或是 `padding-bottom` 為 % 數，這樣就可以讓高度和寬度做等比例縮放，而 iframe 則是使用 `position: absolute` 滿版定位在容器裡面。
以影片寬高比 16:9 為例，高度為寬度的 9/16 倍，因此設定 `padding-bottom: 56.25%;`


## 範例程式碼

<!-- more -->

```html=
<div class="c-video">
  <iframe class="c-video_child" src="https://www.youtube.com/embed/by4SYYWlhEs"></iframe>
</div>
```

```css=
.c-video {
  position: relative;
  height: 0;
  padding-bottom: 56.25%;
}

.c-video_child {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
}
```

Codepen 範例
https://codepen.io/deanocean/pen/porQqeE



以上