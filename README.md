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
| 资产盘点 Family Asset | 家庭资产负债表 App，真实截图 + 月度快照/净资产趋势/双机同步功能 |
| 理念区 | 隐私优先 / 无需服务器 / 持续打磨 |
| 下载区 | 两个下载卡片（均指向本站 APK 直链） |
| 页脚 | GitHub 链接 |

## 下载 APK

两个 APK 都放在本站 `downloads/` 目录，通过 Pages 直链下载，无需令牌：

- 书迹 ReadTrace v0.7.0：`downloads/readtrace-v0.7.0.apk`（约 17MB）
- 资产盘点：`downloads/family-asset-inventory.apk`（约 2.5MB）

页面底部 `DOWNLOAD_URLS` 配置指向这两个相对路径。

## 如何修改

### 1. 更换 APK

把新 APK 覆盖到 `downloads/` 目录同名文件即可；若改文件名，同步修改 `index.html` 底部 `DOWNLOAD_URLS`。

### 2. 更新文案 / 截图

全部内容都在 `index.html` 中，直接编辑对应文字即可。截图以 base64 内联，如需替换：

1. 把新图压缩到 460px 宽、JPEG，放入 `assets/`
2. 用 base64 替换 HTML 中对应的 `data:image/jpeg;base64,...` 片段

### 3. 本地预览

```bash
cd app-showcase
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000
```

> 注意：本地 `index.html` 已是内联版本，直接双击也能看（下载按钮的相对路径在本地指向本地 downloads 目录）。

### 4. 更新线上页面

修改后提交推送，GitHub Pages 会自动重新构建（约 1-2 分钟生效）：

```bash
git add -A && git commit -m "update: 更新宣传页" && git push
```

## 技术说明

- 单 HTML 文件，CSS/JS 全部内联
- 8 张截图以 base64 内联，页面完全自包含
- 响应式设计（移动优先），360 / 390 / 1440 宽度均无横向溢出
- 无障碍：语义化标签、焦点样式、`prefers-reduced-motion` 支持
- 字体：Fraunces（拉丁展示）+ Noto Serif SC（中文），Google Fonts 加载，带本地降级字体栈
- 视觉：书迹 App 用墨绿金铜色系，资产盘点 App 用蓝色系，两套视觉语言呼应各自产品
