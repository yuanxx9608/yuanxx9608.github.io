# 两款应用 · 宣传页

一个单文件、自包含的宣传落地页，展示两款 Android 应用并引导下载。

- **线上地址**：https://yuanxx9608.github.io/
- **源码仓库**：https://github.com/yuanxx9608/yuanxx9608.github.io
- **页面文件**：`index.html`（所有图片已 base64 内联，无外部图片依赖）

## 页面内容

| 区块 | 说明 |
|---|---|
| Hero | 主标语「把日子，过得更有数」+ 双手机叠放展示 |
| 书迹 ReadTrace | 阅读统计 App，4 项功能 + 4 张真实截图画廊 |
| 资产盘点 AssetTrack | 资产管理 App（CSS 绘制示意图 + 占位文案） |
| 理念区 | 隐私优先 / 无需服务器 / 持续打磨 |
| 下载区 | 两个下载卡片 |
| 页脚 | GitHub 链接 |

## 如何修改

### 1. 替换下载链接（重要）

打开 `index.html`，找到底部的 `<script>` 中的 `DOWNLOAD_URLS`：

```js
const DOWNLOAD_URLS = {
  readtrace: "https://github.com/yuanxx9608/weread-readtrace/releases/latest",
  assettrack: "https://github.com/yuanxx9608/asset-inventory/releases/latest"
};
```

把两个 URL 换成你的真实 APK 下载地址（GitHub Releases、蓝奏云、官网等均可）。

> 建议为每个 App 建一个 GitHub Release 并上传 APK，链接形如：
> `https://github.com/<用户>/<仓库>/releases/download/v1.0/app.apk`

### 2. 更新资产盘点 App 的信息

资产盘点 App 当前是示意内容。在 `index.html` 中搜索 `placeholder-note` 和 `资产盘点` 相关文案即可替换：

- 左侧 `mock-phone` 是一段用 CSS/HTML 绘制的手机示意图。如果有真实截图，把整个 `<div class="mock-phone">...</div>` 换成 `<img src="截图地址">` 即可。
- 功能文案位于 `asset-content` 区块的 `.feature` 里。
- 去掉 `placeholder-note` 那个黄色提示框即可隐藏「示意占位」说明。

### 3. 本地预览

```bash
cd app-showcase
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000
```

### 4. 更新线上页面

修改 `index.html` 后提交推送即可，GitHub Pages 会自动重新构建（约 1-2 分钟生效）：

```bash
git add index.html README.md
git commit -m "update: 更新宣传页"
git push
```

## 技术说明

- 单 HTML 文件，CSS/JS 全部内联
- 4 张截图以 base64 内联，页面完全自包含
- 响应式设计（移动优先），桌面/手机均适配
- 无障碍：语义化标签、焦点样式、`prefers-reduced-motion` 支持
- 字体：Fraunces（拉丁展示）+ Noto Serif SC（中文），Google Fonts 加载，带本地降级字体栈
