# 📊 MarketGlance

一个专为多屏、暗光及复盘环境打造的**全球资产全景量化看板**。

通过原生的动态节点注入与高级沙盒隔离技术，实现 A股、美股标普500 以及加密货币（Crypto）大盘云图的 **100% 全屏自适应无缝平铺**。纯前端单文件架构，零服务器依赖，即开即用。

---

## ✨ 核心特性

- 🌐 **三位一体全球视野**：
  - 🇨🇳 **A股/ETF 行业热力图**：深度集成 `52etf.site` 的多维板块与资金下钻视图。
  - 🇺🇸 **美股大盘云图**：基于 TradingView 官方白名单 Standard 接口，实时追踪标普 500（`SPX500`）核心权重股。
  - 🪙 **Crypto 泡泡图**：穿透式无缝嵌入 `Crypto Bubbles` 高性能三维量化气泡图。
- 🛠️ **硬核全屏无感渲染**：
  - 针对 TradingView 等小部件在选项卡切换（`display: none`）时高度坍缩变为 0 导致渲染崩溃的经典 Bug，自研了**动态解构重组机制**。
  - 极致暗黑护眼底色（`#0d1117`），极大程度缓解长时间看盘的视觉疲劳。
- ⚡ **零成本极致轻量**：
  - 纯原生 HTML5 / JavaScript，结合 Tailwind CSS 现代化公用类。
  - **不需编译、不需安装、不需服务器**，可直接作为静态页面通过 GitHub Pages 10秒内完成全球 CDN 免费部署。

---

## 🛠️ 本地快速开始

1. 下载或复制代码库中的 `index.html`。
2. 在任意操作系统（Windows / macOS / Android / iOS）上**双击该文件**即可直接在浏览器中开始看盘。

---

## 🚀 免费一键托管 (GitHub Pages)

如果你希望随时随地通过手机、平板、或多台电脑访问这个看盘网站，可以利用 GitHub 免费托管：

1. **新建仓库**：在 GitHub 创建一个公开的（Public）仓库，命名为 `market-glance`。
2. **上传代码**：将 `index.html` 上传至该仓库的根目录下。
3. **开启 Pages**：进入仓库的 `Settings` -> `Pages`，将 Source 分支设置为 `main` 并保存。
4. **即刻访问**：1分钟后，通过 `https://<你的用户名>.github.io/market-glance/` 即可全球秒开你的专属盘面。

---

## 💡 避坑技术内幕

* **为什么不使用 Iframe 嵌套美股网站（如 Finviz）？**
  绝大多数国际主流财经网站（如 Finviz、Yahoo Finance）都在服务器端部署了严格的 `X-Frame-Options: SAMEORIGIN` 防盗链策略。本项目放弃了常规的 iframe 嵌套，转而采用 TradingView 官方开放的白名单 `embed-widget-stock-heatmap.js` 异步脚本，通过运行时（Runtime）注入动态节点，完美绕过了这一拦截。

* **强效 CSS 穿透**：
  由于第三方脚本在加载时会疯狂生成层级未知的嵌套 `div`，代码在顶层 CSS 中使用了最高权重的强力穿透限制：
  ```css
  #view-container, .tradingview-widget-container, .tradingview-widget-container div, iframe {
      width: 100% !important;
      height: 100% !important;
  }
