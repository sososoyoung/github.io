---
title: 网页常用分享相关meta设置
date: 2018-03-31 16:17:15
tags: share, twitter share, facebook share
categories: share, web
---

web 开发经常需要面对  各种分享的需求， 下面总结了一些分享落地页需要设置的信息

# 相关链接

1.  facebook [** debug **](https://developers.facebook.com/tools/debug/), [doc](https://developers.facebook.com/docs/sharing/best-practices/?locale=zh_CN),
1.  twitter: [** debug **](https://cards-dev.twitter.com/validator), [Summary Card](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/summary), [summary_large_image Card](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/summary_large_image)

# 页面设置

```html
<!-- twitter setting -->
<meta name="twitter:card" content="${card_type}">
<meta name="twitter:site" content="${site_name}" />
<meta property="twitter:title" content="${title}">
<meta property="twitter:image" content="${image_url}">
<meta property="twitter:image:alt" content="${image_alt}">
<meta property="twitter:description" content="${description}">
<meta property="twitter:app:id:iphone" content="${apple_store_id}">
<meta property="twitter:app:id:googleplay" content="${googleplay_id}">
<!-- facebook setting -->
<meta property="fb:app_id" content="${app_id}">
<!-- open graph -->
<meta property="og:type" content="website">
<meta property="og:site_name" content="${site_name}" />
<meta property="og:url" content="${website_url}">
<meta property="og:image" content="${image_url}">
<meta property="og:image:width" content="${image_width}">
<meta property="og:image:height" content="${image_height}">
<meta property="og:title" content="${description}">
<meta property="og:description" content="${description}">
<!-- article -->
<meta property="article:tag" content="${tag}" />
<meta property="article:publisher" content="${publisher}" />
<meta property="article:author" content="${author}" />
```

# UI 图片准备：

### 1. facebook:

> 大小：<=8MB
> 比例：1.91:1 宽高比大尺寸： 推荐: 1200x630, 最低：600x315
> 小尺寸： 200x200

### 2. twitter: 

* 长方形:

  > 大小：<=5MB
  > 比例： 2:1 宽高比大尺寸：4096x4096
  > 小尺寸：300x157
  > 格式：JPG, PNG, WEBP and GIF

* 正方形:
  > 大小：<=5MB
  > 比例： 1:1 宽高比尺寸： 最大: 4096x4096, 最小：144x144
  > 格式：JPG, PNG, WEBP and GIF

# 文案准备

注：Facebook 不支持分享传入 title，twitter 可以预制一段用户分享的文案

分享卡片信息：

> title：不包含品牌名称或未提及域名的清晰标题。
> description： 清楚的说明，至少包含两个句子。
> simage:alt：<= 420 characters.
