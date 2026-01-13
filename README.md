# IP Sentinel (IP 哨兵) - Cloudflare Worker
**IP Sentinel** 是一个运行在 Cloudflare Workers 上的单文件网络检测工具。它集成了 IP 查询、网络连通性测试、WebRTC 隐私检测、风险评分以及 PWA 支持，界面采用现代化的 React + Tailwind CSS 构建。

** 演示地址： [IP Sentinel](https://ip.wanouge.com)。

## ✨ 主要特性

* **🌍 多维度 IP 信息**: 显示客户端 IP、国家/城市、ISP（运营商）、ASN、数据中心信息及经纬度。
* **⚡ 网络连通性测试**:
* 自动识别网络环境（中国大陆/海外）。
* **海外**: 检测 Google, YouTube, OpenAI, GitHub 等连通性。
* **国内**: 检测 百度, Bilibili, 抖音, 微信 等连通性。


* **🛡️ 隐私与安全**:
* **WebRTC 检测**: 检测是否存在真实 IP 泄露。
* **代理/风险评分**: 基于 `ipapi.is` 检测是否为 VPN、代理、Tor 节点或数据中心 IP，并显示风险评分。


* **📱 优秀的 UI/UX**:
* 基于 Tailwind CSS 的暗黑模式设计 (Dark Mode)。
* **PWA 支持**: 支持添加到手机主屏幕，像原生 App 一样使用。
* **地图集成**: Google Maps 嵌入显示 IP 位置（中国大陆 IP 显示静态信息）。
* **多语言**: 支持 中文/English 一键切换。


* **🚀 极速部署**: 纯 Cloudflare Worker 实现，无需服务器，零成本托管。

## 🛠️ 技术栈

* **Runtime**: [Cloudflare Workers](https://workers.cloudflare.com/)
* **Frontend**: React 18 (CDN 引入), Tailwind CSS (CDN 引入)
* **External APIs**:
* Cloudflare `request.cf` (主要地理位置数据)
* `api.ipapi.is` (风险评分与 ASN 信息)
* `ip.sb` (IPv4/IPv6 详情)
* `ping0.cc` (网络分析)


## 🚀 部署指南 (快速上手)

最简单的部署方式是直接在 Cloudflare Dashboard 上操作，无需本地环境。

### 如何部署：直接复制 (最快)

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)。
2. 进入左侧菜单的 **Workers & Pages**。
3. 点击 **Create Application** -> **Create Worker**。
4. 为你的 Worker 起个名字（例如 `ip-sentinel`），点击 **Deploy**。
5. 部署完成后，点击 **Edit code**。
6. 打开你本地的 `Worker.js` 文件，全选并复制所有代码。
7. 在 Cloudflare 编辑器中，删除原有的 `worker.js` 内容，粘贴你刚才复制的代码。
8. 点击右上角的 **Deploy** 保存。

### ⚙️ 个性化配置 (环境变量)

无需修改代码，你可以直接在 Cloudflare 后台设置以下变量来修改网站信息。

1. 在 Worker 详情页，点击 **Settings** -> **Variables and Secrets**。
2. 点击 **Add variable**，添加以下变量（按需添加，不填则显示默认值）：

| 变量名称 | 含义 | 示例值 |
| --- | --- | --- |
| `TITLE` | 网页标题 | IP SENTINEL |
| `NAME` | 英文名称 (显示在副标题) | DollSenior |
| `NAMECN` | 中文名称 (显示在副标题) | 玩偶学长 |
| `SHORT` | 英文简称 (连接状态标签) | DollSenior |
| `SHORTCN` | 中文简称 (连接状态标签) | 玩偶🧸 |
| `DIBUEN` | 底部版权文字 (英文) | IP SENTINEL · DollSenior Edition |
| `DIBUCN` | 底部版权文字 (中文) | IP SENTINEL · 玩偶学长定制版 |

3. 添加完成后，**必须**返回顶部再次点击 **Deploy**，配置才会生效。
4. 访问分配给你的 `*.workers.dev` 域名即可使用！

## 关于 API 限制

本项目使用了一些免费的第三方 API（如 `ipapi.is`）。这些服务通常有速率限制（Rate Limit）。如果是个人使用通常没问题，如果访问量巨大，建议自行更换为付费 API 或自行搭建后端。

## 📝 免责声明

* 本项目集成的 `request.cf` 属性依赖于 Cloudflare 的 IP 数据库，位置信息仅供参考。
* 项目源码中包含的第三方 API 服务与其拥有者无关，请遵守各 API 的使用条款。

## 🤝 贡献与支持

如果你喜欢这个项目，欢迎：
* 在 GitHub 上给我点一颗 **Star** ⭐
* 提交 Issue 或 Pull Request
* 分享给你的朋友

## 👏 致谢

* 原作者/定制版标识: **DollSenior (玩偶学长)**
* UI 设计灵感来源于开源社区优秀的 IP 工具箱项目。

