---
abbrlink: e5a5d29d
categories:
- - 测试
date: '2024-12-21T21:56:21+08:00'
tags:
- 测试
title: hexo笔记
updated: '2024-12-22T15:01:56.813+08:00'
---
测试看看

Qexo有用吗

咋回事啊

## 一個圖庫集合。

寫法
PLAINTEXT

```html
<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>
```html
<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>

```


| 參數        | 解釋                 |
| ----------- | -------------------- |
| name        | 圖庫名字             |
| description | 圖庫描述             |
| link        | 連接到對應相冊的地址 |
| img-url     | 圖庫封面的地址       |

---

## 文章模板

```markdown
---
title:
date:
updated:
tags:
categories:
keywords:
description:
top_img:
comments:
cover:
toc:
toc_number:
toc_style_simple:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
abcjs:
noticeOutdate:
---
```markdown
---
title:
date:
updated:
tags:
categories:
keywords:
description:
top_img:
comments:
cover:
toc:
toc_number:
toc_style_simple:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
abcjs:
noticeOutdate:
---

```


| 寫法        | 解釋                             |
| ----------- | -------------------------------- |
| title       | 【必需】文章標題                 |
| date        | 【必需】文章創建日期             |
| updated     | 【可選】文章更新日期             |
| tags        | 【可選】文章標籤                 |
| categories  | 【可選】文章分類                 |
| keywords    | 【可選】文章關鍵字               |
| description | 【可選】文章描述                 |
| top_img     | 【可選】文章頂部圖片             |
| cover       | 【可選】文章縮略圖(如果沒有設置) |

---

## 页面模板

```markdown
---
title:
date:
updated:
type:
comments:
description:
keywords:
top_img:
mathjax:
katex:
aside:
aplayer:
highlight_shrink:
random:
limit:
  type:
  value:
---
```markdown
---
title:
date:
updated:
type:
comments:
description:
keywords:
top_img:
mathjax:
katex:
aside:
aplayer:
highlight_shrink:
random:
limit:
  type:
  value:
---

```

这个是页面模板


| 參數             | 解釋                                                                                |
| ---------------- | ----------------------------------------------------------------------------------- |
| title            | 【必需】頁面標題                                                                    |
| date             | 【必需】頁面創建日期                                                                |
| type             | 【必需】標籤、分類和友情鏈接三個頁面需要配置                                        |
| updated          | 【可選】頁面更新日期                                                                |
| description      | 【可選】頁面描述                                                                    |
| keywords         | 【可選】頁面關鍵字                                                                  |
| comments         | 【可選】顯示頁面評論模塊 (默認 true)                                                |
| top_img          | 【可選】頁面頂部圖片                                                                |
| mathjax          | 【可選】顯示 mathjax (當設置 mathjax 的 per_page: false 時，才需要配置，默認 false) |
| katex            | 【可選】顯示 katex (當設置 katex 的 per_page: false 時，才需要配置，默認 false)     |
| aside            | 【可選】顯示側邊欄 (默認 true)                                                      |
| aplayer          | 【可選】在需要的頁面加載 aplayer 的 js 和 css，請參考文章下面的音樂配置             |
| highlight_shrink | 【可選】配置代碼框是否展開 (true/false) (默認為設置中 highlight_shrink 的配置)      |
| random           | 【可選】配置友情鏈接是否隨機排序（默認為 false）                                    |
| limit            | 【可選】配置説説顯示數量                                                            |
| limit.type       | 【可選】配置説説顯示數量的類型 （date 或者 num）                                    |
| limit.value      | 【可選】配置説説顯示數量的值                                                        |

---

## 子页面

子頁面也是普通的頁面，你只需要 hexo n page xxxxx 創建你的頁面就行

然後使用標簽外掛 gallery，具體用法請查看對應的內容。

{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
![](https://i.loli.net/2019/12/25/gEy5Zc1Ai6VuO4N.jpg)
![](https://i.loli.net/2019/12/25/d6QHbytlSYO4FBG.jpg)
![](https://i.loli.net/2019/12/25/6nepIJ1xTgufatZ.jpg)
![](https://i.loli.net/2019/12/25/E7Jvr4eIPwUNmzq.jpg)
![](https://i.loli.net/2019/12/25/mh19anwBSWIkGlH.jpg)
![](https://i.loli.net/2019/12/25/2tu9JC8ewpBFagv.jpg)
{% endgallery %}
[{"url":"https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg","alt":""},{"url":"https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg","alt":""},{"url":"https://i.loli.net/2019/12/25/gEy5Zc1Ai6VuO4N.jpg","alt":""},{"url":"https://i.loli.net/2019/12/25/d6QHbytlSYO4FBG.jpg","alt":""},{"url":"https://i.loli.net/2019/12/25/6nepIJ1xTgufatZ.jpg","alt":""},{"url":"https://i.loli.net/2019/12/25/E7Jvr4eIPwUNmzq.jpg","alt":""},{"url":"https://i.loli.net/2019/12/25/mh19anwBSWIkGlH.jpg","alt":""},{"url":"https://i.loli.net/2019/12/25/2tu9JC8ewpBFagv.jpg","alt":""}]
如果你想要使用 /photo/ohmygirl 這樣的鏈接顯示你的圖片內容

你可以把創建好的 ohmygirl 整個文件夾移到 photo 文件夾裏去
