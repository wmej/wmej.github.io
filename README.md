# 立冬 · 写给 Zwm

给 Zwm 的立冬日记页，署名 Wmej。拼贴手账风格：牛皮纸底、纸片、胶带、印章、真实奶龙照片贴纸。

## 页面里有什么

| 区块 | 内容 | 互动 |
| --- | --- | --- |
| 封面 | 「把冬天贴进日记」+ 奶龙照片 | 点照片切换奶龙表情、随机说一句话 |
| 01 冬天时间线 | 立冬 → 小雪 → 大雪 → 冬至 → 平安夜 → 跨年，六个未来节点 | 点开每个节点读提前写好的话，计数 0/6，读完有完成提示 |
| 02 五个问题 | 冬天想做什么、不开心时希望怎样、被惹到希望怎么处理等 | 逐题选择、可回看，最后生成「Zwm 的冬天说明书」，可一键复制发微信 |
| 03 想对你说 | 关于「有不满直接说、别让我猜」的那段话 | 常驻展示，不隐藏 |
| 04 今天的心情 | 五种心情 + 留言 | 保存到本机 localStorage，刷新后还在；每条可复制或删除 |
| 结尾 | 立冬快乐 + 署名 + 奶龙 | 回到开头 |

第 5 题如果选「先忍着」，结果页会额外提示去看第 03 段——把互动和那段话连起来。

## 文件结构

```
.
├── index.html              整站（HTML + CSS + JS）
├── favicon.svg             站点图标
├── assets/
│   ├── nailong-a.png       奶龙（招手）
│   └── nailong-b.png       奶龙（惊讶）
├── .nojekyll               关掉 Jekyll
└── README.md
```

## 奶龙素材来源

按「网上找 → 生成 → SVG」的顺序，这次在第一步就找到了可用素材：

- 来源：萌娘百科共享资源「奶龙」分类
  https://commons.moegirl.org.cn/Category:%E5%A5%B6%E9%BE%99
- 使用了两张官方 3D 形象图（招手、惊讶），本地保存为 `assets/nailong-a.png`、`assets/nailong-b.png`
- 原图是白底，已用脚本做背景去除并裁边，页面里作为「照片贴纸」使用
- 版权归原著作权人所有。本页仅用于个人、非商业的私人祝福；如果要公开传播或商用，请换成官方授权素材或自制图

## 部署到 GitHub Pages

仓库名必须是 `wmej.github.io`：

```bash
git init
git add .
git commit -m "lidong for Zwm"
git branch -M main
git remote add origin https://github.com/wmej/wmej.github.io.git
git push -u origin main
```

仓库 **Settings → Pages**：Source 选 `Deploy from a branch`，Branch 选 `main` / `/ (root)`，保存后等 1–2 分钟，访问 `https://wmej.github.io`。

## 改内容

- **时间线**：搜 `11.07`、`12.31`，改日期、节气名和正文
- **问题**：搜 `var QS =`，每题有 `a` / `b` 两个选项和对应的结果文案
- **那段话**：搜 `一段认真的话`
- **心情选项**：搜 `data-mood`
- **名字 / 日期**：搜 `Zwm`、`Wmej`、`2026.11.07`

## 改配色

`index.html` 顶部 `:root`：

```css
--kraft: #E8DCC8;   /* 牛皮纸底 */
--paper: #F7F0E3;   /* 纸片 */
--ink: #2A241C;     /* 正文 */
--rust: #B4553A;    /* 锈红 */
--moss: #6E7B5B;    /* 苔绿 */
--muted: #8A7A64;   /* 次要文字 */
```

## 数据说明

- 问答答案只存在页面内存里，刷新就没了；点「复制这份说明书」可以发出去
- 心情留言存在浏览器 localStorage（`lidong_notes_v1`），只在这台设备上，不会上传
- 没有后端、没有统计、没有外链请求

## 本地预览

直接双击 `index.html`，或：

```bash
python -m http.server 8080
# http://localhost:8080
```

## 常见问题

- **复制没反应**：微信里可能限制剪贴板，长按「冬天说明书」里的文字手动复制即可
- **留言没了**：清浏览器数据、换设备或无痕模式都会丢，留言只在本机
- **国内访问慢**：`github.io` 不稳定，可镜像到 Cloudflare Pages / Vercel，代码不用改
