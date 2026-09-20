# 直升机空气动力学 · 学习笔记

以《直升机空气动力学》（招启军、徐国华、王博 著）为主线的**个人学习笔记站点**，采用 [docsify](https://docsify.js.org/) 构建，通过 GitHub Actions 自动部署到 GitHub Pages。

## 站点入口

> ### [ranbot1.github.io/Helicopter-aerodynamics](https://ranbot1.github.io/Helicopter-aerodynamics/)

已上线。也可以直接点这里进仓库看源码：[Ranbot1/Helicopter-aerodynamics](https://github.com/Ranbot1/Helicopter-aerodynamics)

## 站点特性

- 左侧三级目录（篇 → 章 → 小节），页面内标题自动生成锚点
- 深色 / 浅色模式一键切换，偏好本地记忆
- 公式用 KaTeX 渲染，关系图用 Mermaid 渲染
- 每章配可折叠思维导图，支持打印为 PDF
- 底部「上一节 / 下一节」连续阅读

## 目录结构

```
.
├── README.md                       仓库说明（本文件）
├── .github/workflows/pages.yml     Pages 自动部署工作流
└── docs/                           GitHub Pages 发布目录
    ├── .nojekyll                   关闭 Jekyll，保证 _sidebar.md 可访问
    ├── index.html                  docsify 配置入口
    ├── _sidebar.md                 左侧目录
    ├── README.md                   站点首页
    ├── assets/site.css             站点样式（含暗色主题）
    ├── chapter1/
    │   ├── README.md               第 1 章正文章节页
    │   ├── mindmap.md              第 1 章思维导图页
    │   └── ch1-mindmap.html        可折叠思维导图（供 iframe 嵌入）
    ├── chapter2/ …                第 2–12 章（占位页，含原书目录结构）
    └── appendix/
        ├── symbols.md              术语与符号速查
        └── formulas.md             常用公式清单
```

## 本地预览

站点是纯静态页面，任意静态服务器都可以。在仓库根目录执行：

```bash
python -m http.server 8080 --directory docs
```

然后打开 <http://localhost:8080>。

> 注意：不要直接双击 `docs/index.html`。docsify 通过 fetch 加载 Markdown，`file://` 协议下会被浏览器拦截。

## 部署方式

本站采用 **GitHub Actions** 模式：`.github/workflows/pages.yml` 会在每次推送到 `main` 时，把 `docs/` 目录打包上传并发布。

```
push to main  →  checkout  →  configure-pages  →  upload docs/  →  deploy-pages
```

也就是说，**改完内容直接 `git push`，站点会自动重新部署**，不需要任何手工操作。部署进度可在 [Actions 页面](https://github.com/Ranbot1/Helicopter-aerodynamics/actions) 查看。

如果哪天想换成更简单的分支发布模式，改用：**Settings → Pages → Source** 选 `Deploy from a branch` → 分支 `main` + 目录 `/docs`，然后删掉 `.github/workflows/pages.yml` 即可。两种模式都不要动 `docs/.nojekyll`。

## 如何继续补充章节

1. 在 `docs/chapterN/README.md` 中按「本章导览 → 分节正文 → 图表与公式 → 本章小结 → 自测题」的结构写入内容。
2. 需要思维导图时，新建 `docs/chapterN/chN-mindmap.html`，再建 `mindmap.md` 用 iframe 嵌入。
3. 如果新增了页面，记得在 `docs/_sidebar.md` 里补上链接。
4. `git push`，等 Actions 跑完即可。

## 说明

本仓库为个人学习整理，不替代原书。正文中的概念、数据、型号与年份对照原书核对；表述、图表与组织方式为整理者所加，深入推导请以原书为准。
