+++
date = '2025-06-16T13:10:00+08:00'
tags = ["PaperMod主题"]
title = 'Hugo PaperMod主题个性化修改美化总结'
description = 'Hugo PaperMod主题个性化修改美化总结'
keywords = ["Hugo", "博客", "美化", "Papermod主题"]
ShowToc= true
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
可以参考 [Yunpeng Tai](https://yunpengtai.top/posts/hugo-journey/#%e5%ad%97%e4%bd%93) ，真的很方便！

## 版权声明 & 隐私政策

下面以版权声明为例，其他页面同理

1. 新建 layouts/copyright/single.html

```
{{ define "main" }}
<main id="main" class="main-content" role="main">
  <article class="post-single">
    <header class="post-header">
      <h1 class="post-title">{{ .Title }}</h1>
    </header>

    <div class="post-content">
      {{ .Content }}
    </div>
  </article>
</main>
{{ end }}
```

2. 新建 content/copyright.md

```
---
title: "版权声明"
url: "/copyright/"
layout: "copyright"
summary: copyright
---

本博客（**Avery's Blog**）所有原创内容采用 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) 协议共享。

欢迎在注明来源的前提下非商业转载，禁止用于 AI 模型训练及商业用途。
```
3. 复制 themes/PaperMod/layouts/partials/footer.html 的文件

把它放到你的 layouts/partials/footer.html 中并将第一部分区域替换为下方所示

```
{{- if not (.Param "hideFooter") }}
<footer class="footer">
    <span>&copy; {{ now.Year }} <a href="/about/">Avery</a></span>
    <span>·&nbsp;<a href="/privacy/">隐私政策</a></span>
    <span>·&nbsp;<a href="/copyright/">版权说明</a></span>
    <span>
        Powered by
        <a href="https://gohugo.io/" rel="noopener noreferrer" target="_blank">Hugo</a> &
        <a href="https://github.com/loyayz/hugo-PaperModx/" rel="noopener" target="_blank">PaperModx</a>
    </span>

</footer>
{{- end }}
```
即可在站点的页脚处看到，任务完成！








