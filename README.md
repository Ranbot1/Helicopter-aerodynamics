# 直升机空气动力学 · 学习笔记

以《直升机空气动力学》（招启军、徐国华、王博 著）为主线的**个人学习笔记站点**，采用 [docsify](https://docsify.js.org/) 构建，直接部署在 GitHub Pages 上。

站点入口：`https://ranbot1.github.io/Helicopter-aerodynamics/`（开启 Pages 后生效）

## 站点特性

- 左侧三级目录（篇 → 章 → 小节），页面内标题自动生成锚点
- 深色 / 浅色模式一键切换，偏好本地记忆
- 公式用 KaTeX 渲染，关系图用 Mermaid 渲染
- 每章配可折叠思维导图，支持打印为 PDF
- 底部「上一节 / 下一节」连续阅读

## 目录结构

```
.
├── README.md                仓库说明（本文件）
└── docs/                    GitHub Pages 发布目录
    ├── .nojekyll            关闭 Jekyll，保证 _sidebar.md 可访问
    ├── index.html           docsify 配置入口
    ├── _sidebar.md          左侧目录
    ├── README.md            站点首页
    ├── assets/site.css      站点样式（含暗色主题）
    ├── chapter1/
    │   ├── README.md        第 1 章正文章节页
    │   ├── mindmap.md       第 1 章思维导图页
    │   └── ch1-mindmap.html 可折叠思维导图（供 iframe 嵌入）
    ├── chapter2/ …         第 2–12 章（占位页，含原书目录结构）
    └── appendix/
        ├── symbols.md       术语与符号速查
        └── formulas.md      常用公式清单
```

## 本地预览

站点是纯静态页面，任意静态服务器都可以。在仓库根目录执行：

```bash
python -m http.server 8080 --directory docs
```

然后打开 <http://localhost:8080>。

> 注意：不要直接双击 `docs/index.html`。docsify 通过 fetch 加载 Markdown，`file://` 协议下会被浏览器拦截。

## 部署到 GitHub Pages

1. 把本仓库推送到 GitHub（分支 `main`）。
2. 打开仓库 **Settings → Pages**。
3. **Source** 选择 `Deploy from a branch`；**Branch** 选择 `main`，目录选择 **`/docs`**，保存。
4. 等待 1–2 分钟，访问 `https://<你的用户名>.github.io/Helicopter-aerodynamics/`。

`docs/.nojekyll` 已就位，无需额外配置。首次部署后如果样式没生效，清一下浏览器缓存再试。

## 如何继续补充章节

1. 在 `docs/chapterN/README.md` 中按「本章导览 → 分节正文 → 图表与公式 → 本章小结 → 自测题」的结构写入内容。
2. 需要思维导图时，新建 `docs/chapterN/chN-mindmap.html`，再建 `mindmap.md` 用 iframe 嵌入。
3. 如果新增了页面，记得在 `docs/_sidebar.md` 里补上链接。

## 说明

本仓库为个人学习整理，不替代原书。正文中的概念、数据、型号与年份对照原书核对；表述、图表与组织方式为整理者所加，深入推导请以原书为准。
