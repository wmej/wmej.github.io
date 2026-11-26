# 站点维护说明

给这个仓库用的开发文档。站点本身的介绍见 [README.md](README.md)。

## 视觉规范

| 用途 | 色值 |
| --- | --- |
| 背景 | `#FDFCFA` |
| 站点名 / 标题 | `#1F1D1A` |
| 正文 | `#3A3733` |
| 次要文字（日期、页脚） | `#6F6A62` |
| 强调 / 链接 | `#B5462F` |
| 分隔线 | `#ECE7E0` |

正文 17px、行高 1.9，栏宽 700px；手机端字号降到 16px。

字体是衬线：`Georgia, "Songti SC", "STSong", "Noto Serif SC", "Source Han Serif SC", SimSun, serif`。西文落 Georgia，中文在 Mac 上落到宋体（Songti SC），Windows 上落到 SimSun。

## 文件结构

```
.
├── index.html       首页：介绍 + 文章列表
├── about.html       关于 + 最近 + 联系方式
├── posts/
│   └── name.html    关于名字
├── style.css        全部样式
├── favicon.svg      站点图标
├── .nojekyll        关掉 Jekyll
├── README.md        仓库首页的个人介绍
└── DEVELOPMENT.md   本文件
```

## 加一篇新文章

1. 复制 `posts/name.html`，改名（例如 `posts/new-post.html`）。
2. 改这几处：
   - `<title>标题 - Wmej</title>` 和 `<meta name="description">`
   - `.post-title` 里的标题、`.post-meta` 里的日期和分类
   - `.post-body` 里的正文
3. 在 `index.html` 里加一个 `<article class="entry">` 块，放在最上面（最新的在前）。

## 改配色 / 排版

全部集中在 `style.css` 顶部的 `:root`：

```css
:root {
  --bg: #FDFCFA;      /* 背景 */
  --ink: #1F1D1A;     /* 标题 */
  --body: #3A3733;    /* 正文 */
  --muted: #6F6A62;   /* 次要文字 */
  --accent: #B5462F;  /* 链接、强调 */
  --line: #ECE7E0;    /* 分隔线 */
}
```

## 部署到 GitHub Pages

仓库名必须是 `wmej.github.io`：

```bash
git add .
git commit -m "update"
git push
```

仓库 **Settings → Pages**：Source 选 `Deploy from a branch`，Branch 选 `master`（或 `main`）/ `/ (root)`，保存后等 1–2 分钟，访问 `https://wmej.github.io`。

## 本地预览

直接双击 `index.html`，或：

```bash
py -3.13 -m http.server 8080
# http://localhost:8080
```
