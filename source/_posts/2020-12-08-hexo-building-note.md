---
title: 使用 HEXO 架設部落格
toc: true
disqusId: some-disqus-id
date: 2020-12-08 03:21:03
categories:
  - 前端
tags:
  - hexo
# cover:
# thumbnail:
# excerpt:
---


## 前言

此部落格是用 [HEXO](https://hexo.io/zh-tw/) 來架設，並佈署在 Github 上。
主題我是使用了 [icarus](https://github.com/ppoffice/hexo-theme-icarus) 再自己寫 CSS 客製化 ，這個主題有中文文件，內容也相當完整。

藉此文章將架設流程及常用指令記錄起來，以便快速查閱。
想知道更多關於 HEXO 的介紹與教學，我在本文最後提供了相關資源供參考。


<!-- more -->


## Hexo 的特色
- 使用 [Markdown](https://markdown.tw/) 語法撰寫。
- 由台灣人開發，中國協作者多，中文資源多。
- 可以部屬在 Github 上，就不需要處理另外花錢買網域。


## 架設流程

### 準備環境
安裝 [Node.js](https://nodejs.org/) 和 [Git](https://git-scm.com/)。 (Node.js 建議安裝 LTS 穩定版)

### 前期安裝

1. 安裝 hexo CLI
```
$ npm install -g hexo-cli
```

2. 建立 hexo 雛形
```
$ hexo init
```

3. 安裝 npm 套件管理工具
```
$ npm install
```


## HEXO 常用指令

查詢 hexo 指令
```
$ hexo
```

建立新文章
```
$ hexo new "My New Post"
// 或是 $ hexo new post ，會產生檔名為 post.md 的檔案
```

開啟模擬伺服器
```
$ hexo s
// 或是 $ hexo server，預設為 localhost:4000
```

建立(編譯)靜態網站
```
$ hexo g 
// 或是 $ hexo generate，會生成 public file
```

部署到遠端伺服器
```
$ hexo d
// 或是 $ hexo deploy，需另外搭配 hexo-deployer-git 之類的套件
```

清除暫存檔案
```
$ hexo clean
// 主要會清除快取檔案 (db.json) 以及編譯檔案 (public)，有時遇到奇怪的問題時可以解決掉
```

## 佈署到 Github

**若要放在 Github 的根目錄**
每個帳戶只有一個能放在最根目錄的專案
> 儲存庫名稱： `{用戶名稱}.github.io`
> 網址： `https://{用戶名稱}.github.io`

**流程**

1. 連接遠端 Github 資料庫
2. 修改 `_config.yml`
```
deploy:
  type: git
  repo: 儲存庫路徑
  branch: gh-pages  // or master
```
3. 安裝 hexo 自動部署工具
```
npm install hexo-deployer-git --save
```
4. 佈署
```
$ hexo d
// 或是 $ hexo deploy
```

## 關於 post

### 我在 post 會用到的 yaml
我自己會加進 `scaffolds/post.md` 裡面，這樣使用 `$ hexo new post` 時就會自動生成
```yaml=
---
title: {{ title }} # 文章標題
date: {{ date }} # 文章日期
toc: true # 開啟文章目錄功能(在 icarus 主題下使用)
categories: # 分類
tags: # 標籤
cover: # 文章大圖
thumbnail: # 文章縮圖
disqusId: some-disqus-id # Disqus 唯一標識，未來更改文章的位置而不會丟失所有評論(安裝留言板 Disqus 時使用)
excerpt: # 文章概要，會顯示在省略文
---
```

※　在文章的 yaml 沒有設定 date 時，預設的文章日期是以檔案生成時間為準。

### 非單一 categories 和 tags 的寫法
```yaml=
categories: # 測試為第一層，哈囉為第二層
  - 測試
  - 哈囉
tags: 
  - 前端文
  - 後端文
```

### 手動設定文章的省略段落
在想要顯示的段落為止加上`<!-- more -->`
```
...想...要...顯...示...的...段...落...

<!-- more -->

...其...餘...的...段...落...
```

### post 的檔案命名
- 最好可以自訂 `年-月-日-文章標題` 的格式來寫： `2020-10-15-這是文章標題.md`
(檔名會影響該文章的網址，所以建議使用英文)
- 檔案前加上下底線 `_` 可以有隱藏效果，文章可以藉此當作草稿功能 `_2020-10-15-這是草稿.md`


## 資源

[六角學院 Youtube - 使用 Hexo 建構個人化部落格](https://www.youtube.com/watch?v=jOJI9ekTzK8&t=4226s)

[第一次架設Hexo網站 | MD工坊](https://magicdogguo.github.io/2019/01/19/%E6%9E%B6%E8%A8%ADHexo%E7%B6%B2%E7%AB%99%E8%8D%89%E7%A8%BF/)

[iT邦幫忙 - hexo相關文章](https://ithelp.ithome.com.tw/tags/articles/hexo)
