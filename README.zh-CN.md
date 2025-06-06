# 🔍 skeb-info
包含心愿单功能的简易 Skeb 信息查询工具 (๑• . •๑)

[English](README.md) | 中文

## 功能特性

- 🔍 通过用户名或链接搜索 Skeb 用户资料
- 📑 显示详细信息，即使创作者关闭请求仍可获取报价和截止时间
- 🔖 使用心愿单来管理追踪收藏的创作者的信息
- ✨ 简洁、用户友好的界面
- 🔗 Skeb 用户信息以及作品信息的 API 代理

## 使用方法

- 访问 [skebinfo.hkra.xyz](https://skebinfo.hkra.xyz/)，输入用户名或链接，点击查询
- 点击用户名称可以打开该用户的 Skeb 主页
- 点击已发送公开委托数量 (`Sent Public Requests`) 的数字可查看该客户按创作者排序的请求数量统计
- 点击书签图标可以将该用户添加到心愿单中。添加后，页面底部会出现心愿单部分
- 在心愿单列表可以打开该用户的 Skeb 主页，重新排序或删除心愿单中的创作者。点击刷新图标可以更新心愿单

### 提示
- 语言支持：目前支持英文、中文和日文。默认使用系统语言，也可以通过在 URL 后添加后缀手动选择语言（例如 `https://skebinfo.hkra.xyz/ja` 为日文，`en` 为英文，`zh` 为中文）
- 用户名输入：输入包含下划线 (`_`) 的用户名时，可以使用空格代替以方便输入

## 免责声明

本工具为非官方接口，仅用于获取 Skeb 平台公开的创作者信息。使用者须遵守 Skeb 服务条款，禁止滥用服务、进行欺诈行为或侵犯第三方权益。开发者不对任何滥用行为或违反 Skeb 指南导致的后果承担责任。

## API 端点
- 用户信息: `/api/users/<username>`
- 所有作品（创作者）: `/api/users/<username>/works?role=creator`
- 所有发送的请求（客户）: `/api/users/<username>/works?role=client`
    - 数据量过大（超过1200）时需要分片，使用返回数据中 `meta.next` 作为下一部分请求的 URL

## 部署

部署自己的实例以避免速率限制和个人使用。

### Cloudflare Workers
1. 将 HTML 文件（`index.html`、`wishlist.html`）托管在静态托管服务上（例如 GitHub Pages、Cloudflare Pages）
2. 创建并部署 Cloudflare Worker（使用 `wrangler` CLI 或 Cloudflare 控制台）
3. 添加环境变量：
   - `PAGE_URL`: 托管 HTML 文件的 URL（例如 `https://afxr17light.github.io/skeb-info/`）
    - 注意：需要在 `wrangler.toml` 中更改 `PAGE_URL`

### Vercel

- 选择其他框架使用默认配置进行部署即可，包含 API 和前端

## 限制

- 速率限制：用户信息请求每分钟 100 次，作品请求：每分钟 5 次；数据量过大时可能无法完成请求
- 依赖 Skeb API：可能受到限制或出现字段更新等原因导致的不可用

## 协议
MIT
