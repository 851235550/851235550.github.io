## 写作方式

这个仓库已经支持 **GitHub Actions 自动构建 + GitHub Pages 自动发布**。

也就是说：

- 本地不需要全局安装 `hexo-cli`
- 日常可以只维护 `source/_posts` 里的 Markdown
- 推送到 `master` 后，由 GitHub Actions 自动执行构建和发布

当前自动发布工作流位于 [.github/workflows/pages.yml](.github/workflows/pages.yml)。

## 推荐工作流

### 方案一：只写 Markdown，完全交给 GitHub Actions 构建

适合平时只想写文章、不想在本地折腾 Hexo 环境。

1. 在 [source/\_posts](source/_posts) 下新建或编辑 Markdown 文件
2. 提交并推送到 `master`
3. GitHub Actions 自动运行 `npm install` 和 `npm run build`
4. 构建产物发布到 GitHub Pages

这种模式下，你本地甚至不需要预览，也不需要全局安装任何 Hexo 命令。

## 本地预览（可选）

如果你偶尔想在本地预览，也不需要全局安装 `hexo-cli`。

只需要安装项目依赖，然后使用仓库内的 npm scripts：

```bash
npm install
npm run server
```

构建静态文件：

```bash
npm run build
```

清理缓存：

```bash
npm run clean
```

这里执行的是 [package.json](package.json) 里的脚本，不依赖全局 `hexo-cli`。

## 如何新建文章

如果你不想依赖 `hexo new`，最简单的方式就是直接手动新建 Markdown 文件。

例如在 [source/\_posts](source/_posts) 下创建：

```text
20260310-文章标题.md
```

然后写入类似的 Front Matter：

```yaml
---
title: 文章标题
date: 2026-03-10 10:00:00
tags:
	- 随笔
categories:
	- 博客
---
```

正文直接写 Markdown 即可。

## 结论

对你这个仓库来说，**更好的方式就是：**

- 本地只写 Markdown
- 不再全局安装 `hexo-cli`
- 需要预览时才执行 `npm install`
- 正式构建和发布全部交给 GitHub Actions

如果你愿意，我还可以顺手帮你把当前的 GitHub Actions 再优化一下，比如：

- 改成更稳定的 Node LTS 版本
- 优化依赖缓存
- 补一份更适合写作的 README
