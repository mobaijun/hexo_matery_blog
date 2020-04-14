---
title: 'Hexo博客全站变灰[哀悼英雄]'
author: 墨白
top: false
cover: false
toc: true
mathjax: false
tags:
  - CSS
  - null
  - null
categories:
  - Hexo
abbrlink: 1615996625
date: 2020-04-04 13:07:13
img:
coverImg:
password:
summary:
---



>  一般在清明节，全国哀悼日，大地震的日子，以及一些影响力很大的伟人逝世或纪念日的时候，身为站长的我们都会让自己的网站的全部网页变成灰色（黑白色），以表示我们对逝者的悼念。那么今天就说说，通过几行简单的代码，来实现这个功能。 

#### 第一种:改变CSS全局样式

使用matery主题的可以在`\themes\matery\source\css\matery.css`添加以下代码完成全站变灰

~~~CSS
/*深切哀悼抗疫英雄,整个网站变灰*/
html {
    filter: progid:DXImageTransform.Microsoft.BasicImage(grayscale=1);
    -webkit-filter: grayscale(100%);
}
~~~

#### 第二种：在网页的<head>标签内加入以下代码

如果你不想改动CSS文件，你可以通过在网页头部中的<head>标签内部加入内联CSS代码的形式实现网站网页变灰

~~~javascript
<style type="text/css">
html {
filter: progid:DXImageTransform.Microsoft.BasicImage(grayscale=1);
-webkit-filter: grayscale(100%);}
</style>
~~~

