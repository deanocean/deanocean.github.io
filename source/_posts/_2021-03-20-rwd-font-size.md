---
title: 2021-03-20-rwd-font-size
toc: true
disqusId: some-disqus-id
date: 2021-03-19 02:50:10
categories: 
  - 前端
tags:
  - 切版
  - RWD
---

## 前言

針對螢幕寬度時變化時遇到的跑版問題，探討解決方法。

<!-- more -->

## 內文

想要講的東西：
html: 62.5% -> 10px 方便計算

html {
  font-size: calc(100vw/32); -> 100vw = 320px | 320px / 32 = 10px | 在 320px 時為 10px
}

假設桌機 1000px / 平板 768px ~ 1000px / 手機 768px ~ 320px

最常遇到問題的會是在 平板的 區間。希望維持和桌機一樣的設計，但是不要跑版。

以 p標籤 為例，假設跑版 = 折行

範例網站
https://codepen.io/deanocean/pen/wvoLogb