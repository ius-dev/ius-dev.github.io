# ius-dev.github.io

ius-dev 的在线工具集。纯静态页面，托管在 GitHub Pages 上。

设计前提：**所有工具都在浏览器本地运行**，输入内容不上传、不留存，因此可以放心处理日志、报文这类含敏感信息的文本。

## 目录结构

```
.
├── index.html              工具列表首页
├── assets/
│   ├── style.css           全站共享样式（暗色主题 + 工具页通用组件）
│   └── favicon.svg         站点图标
├── tools/
│   ├── xml-unescape.html   XML 转义还原
│   └── coord-distance.html 经纬度距离与相对位置
└── .claude/launch.json     本地预览用的启动配置
```

## 本地预览

直接双击 `index.html` 也能看，但用本地服务器更接近线上行为（相对路径、剪贴板 API 等）：

```bash
python -m http.server 8080
```

然后打开 http://localhost:8080/ 。

## 新增一个工具

1. 在 `tools/` 下新建 `<工具名>.html`。
2. 页面骨架直接抄 `tools/xml-unescape.html`：头部引用 `../assets/style.css`，用
   `.site-header` / `.tool-head` / `.toolbar` / `.panes` / `.pane` / `.tool-footer` 这些
   现成的类，不用自己写样式。
3. 在 `index.html` 的 `.tool-grid` 里加一张 `<a class="tool-card">` 卡片，并把
   `.section-title` 里的 `<span class="count">` 数字 +1。

新增的通用样式（比如第三种面板布局）加到 `assets/style.css` 的工具页通用组件区，
不要写在单个工具页的 `<style>` 里。

## 发布

仓库即站点根目录，推到 `main` 分支后 GitHub Pages 会自动构建。
仓库需在 Settings → Pages 中把 Source 设为 `Deploy from a branch` → `main` / `/ (root)`。
