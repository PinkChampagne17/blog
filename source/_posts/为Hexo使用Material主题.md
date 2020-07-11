---
title: 为Hexo使用Material主题
date: 2020-07-12 00:40:00
categories: 
- Hexo
---

![](https://img2020.cnblogs.com/blog/1981089/202007/1981089-20200712003550454-233983481.png)

[我的Material主题Hexo博客实例](https://pinkchampagne17.github.io/blog/)

# 开始入门

## 下载主题

### 方式一：直接下载源代码
下载后放在theme文件夹里。

**[Download latest release version](https://github.com/bolnh/hexo-theme-material/releases/tag/1.5.6)**

### 方式二：使用Git下载
你可以自己决定想要使用的分支；仅限开发者使用。
```
cd themes
git clone https://github.com/viosey/hexo-theme-material.git material
cd material
git checkout {branch/tags name}
```

## 使用站内搜索插件
安装 [hexo-generator-search](https://github.com/wzpan/hexo-generator-search) 插件。

修改***theme/material*** 目录 `_config.yml` 中的 search值

```YML
search:
    use: local
    swiftype_key: 
```
然后在***主目录***的`_config.yml`文件中添加
```YML
search:
    path: search.xml
    field: all
```

## 修改配置文件
修改***theme/material/layout/_widget/dnsprefetch.ejs***文件，否则会报错，修改内容如下：
```
<% } else if(theme.comment.use.startsWith("disqus")) { %>

// 修改为

<% } else if(theme.comment.use && theme.comment.use.startsWith("disqus")) { %>
```

# 参考资料
1. [bolnh/hexo-theme-material: Material Design theme for hexo.](https://github.com/bolnh/hexo-theme-material)

2. [Hexo + Material + Github 搭建博客与配置](https://www.jianshu.com/p/e551bc71f62c)

3. [hexo s  依旧报错。 · Issue #686 · bolnh/hexo-theme-material](https://github.com/bolnh/hexo-theme-material/issues/686)
