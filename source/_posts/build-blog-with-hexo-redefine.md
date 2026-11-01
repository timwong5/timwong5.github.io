---
title: 用 Hexo + Redefine 搭建简洁的个人博客
date: 2026-11-01 14:00:00
categories:
  - 技术
tags:
  - Hexo
  - 博客
  - GitHub Pages
excerpt: 记录这个博客的搭建过程：Hexo 初始化、Redefine 主题配置、GitHub Actions 自动部署。
---

这篇文章记录一下本站的搭建过程，方便以后重装或迁移时参考。

<!-- more -->

## 技术选型

- 静态生成器：[Hexo](https://hexo.io/)，生态成熟，Markdown 写作体验好
- 主题：[Redefine](https://github.com/EvanNotFound/hexo-theme-redefine)，风格简洁，自带暗色模式、搜索、目录
- 托管：GitHub Pages，通过 GitHub Actions 自动构建发布

## 初始化项目

```bash
npx hexo-cli init blog
cd blog
npm install
npm install hexo-theme-redefine
```

然后把 `_config.yml` 里的 `theme` 改为 `redefine`，并在项目根目录新建 `_config.redefine.yml` 存放主题配置。这样升级主题时不用担心配置被覆盖。

## 让页面更简洁

Redefine 默认功能很多，为了接近“只有头像、简介和文章列表”的效果，我关掉了这些：

```yaml
home_banner:
  enable: false

global:
  website_counter:
    enable: false
  scroll_progress:
    bar: false
    percentage: false

footer:
  runtime: false

comment:
  enable: false
```

并把首页侧栏的第一项设为个人信息：

```yaml
home:
  sidebar:
    first_item: info
```

## 必要的插件

| 插件 | 作用 |
| --- | --- |
| hexo-generator-searchdb | 本地搜索 |
| hexo-wordcount | 字数与阅读时长 |
| hexo-generator-feed | RSS 订阅 |
| hexo-generator-sitemap | 站点地图 |

## 自动部署

在 `.github/workflows/deploy.yml` 里配置 GitHub Actions：推送到 `main` 分支后自动执行 `hexo generate`，再把 `public/` 目录发布到 GitHub Pages。仓库设置里把 Pages 的来源切换为 **GitHub Actions** 即可。

## 日常写作

```bash
hexo new "文章标题"   # 新建文章
hexo server          # 本地预览 http://localhost:4000
git add . && git commit -m "post: 文章标题" && git push
```

推送之后一两分钟，文章就会出现在线上。
