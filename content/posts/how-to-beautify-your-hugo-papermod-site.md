+++
date = '2025-06-16T13:10:00+08:00'
tags = ["PaperMod主题"]
title = 'Hugo PaperMod主题个性化修改美化总结'
description = 'Hugo PaperMod主题个性化修改美化总结'
+++
## 前言

在使用 Hugo PaperMod 主题后，能发现为了达到站点的一些特定的需求，需要做一些个性化的修改。为了让页面更加个性化，本站点参考了一些其他站点的修改方式。那么，本篇文章将重点聚焦一些常用功能的引入和界面的美化，会通过引入一部分相当有价值的链接进行说明，亲测有效。

## 引入 Twikoo 评论系统

1. 先在 hugo.toml 开启 comments = true

2. 在自己的博客目录（非 themes 文件夹内）新建文件 layouts/partials/comments.html 

可以将 themes/layouts/partials/comments.html 的文件复制下来，然后加入下面的代码

```
<!-- Twikoo -->
<div>
    <div class="pagination__title">
        <span class="pagination__title-h" style="font-size: 20px;">评论</span>
        <hr />
    </div>
    <div id="tcomment"></div>
    <script src="https://cdn.jsdelivr.net/npm/twikoo@{{ .Site.Params.twikoo.version }}/dist/twikoo.all.min.js"></script>
    <script>
        twikoo.init({
            envId: "",  //填写自己的envId
            el: "#tcomment",
            lang: 'zh-CN',
            region: 'ap-shanghai',  
            path: 'window.TWIKOO_MAGIC_PATH||window.location.pathname',
        });
    </script>
</div>
```
3. 在站点配置文件 hugo.toml 中加上你的 Twikoo 版本号

```
[params.twikoo]
    version = "1.6.42"  # 版本号需要和你实际使用的 twikoo 版本对应
```

## 字体
可以参考 [Yunpeng Tai](https://yunpengtai.top/posts/hugo-journey/#%e5%ad%97%e4%bd%93) 






