---
title: Markdown 写作速查
date: 2026-11-01 16:00:00
categories:
  - 技术
tags:
  - Markdown
  - 写作
excerpt: 一篇用来检验主题排版效果的 Markdown 语法速查，顺便当作日常写作的参考。
---

这篇文章既是 Markdown 语法速查，也用来检验主题在各种元素下的排版效果。

<!-- more -->

## 标题与段落

段落之间空一行即可。中英文混排时，建议在中文与英文、数字之间加空格，例如：使用 Hexo 7 构建博客。

## 强调

- **粗体**：`**粗体**`
- *斜体*：`*斜体*`
- ~~删除线~~：`~~删除线~~`
- `行内代码`：用反引号包裹

## 列表

有序列表：

1. 第一步
2. 第二步
3. 第三步

任务列表：

- [x] 初始化项目
- [x] 配置主题
- [ ] 写第一篇正经文章

## 引用

> 简单是可靠的前提。
> —— Edsger W. Dijkstra

## 代码块

```python
def fib(n: int) -> int:
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a

print([fib(i) for i in range(10)])
```

```bash
brew install node
npm install -g hexo-cli
```

## 表格

| 语法 | 效果 |
| --- | --- |
| `**text**` | **text** |
| `*text*` | *text* |
| `` `code` `` | `code` |

## 链接与图片

链接：[Hexo 官方文档](https://hexo.io/zh-cn/docs/)

图片语法：`![描述](图片地址)`，开启 `post_asset_folder` 后可以把图片放在与文章同名的目录里。

## 分割线

---

以上就是日常写作会用到的大部分语法。
