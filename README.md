# HaloLight Railway

[![License](https://img.shields.io/badge/license-MIT-green.svg)](./LICENSE)
[![Railway](https://img.shields.io/badge/Railway-Deployed-0B0D0E.svg?logo=railway)](https://halolight-railway.h7ml.cn)
[![Next.js](https://img.shields.io/badge/Next.js-15-%23000000.svg)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-%233178C6.svg)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-19-%2361DAFB.svg)](https://react.dev/)

HaloLight 后台管理系统的 **Railway 一键部署版本**，零配置部署，支持数据库和持久存储。

- 在线预览：<https://halolight-railway.h7ml.cn>
- GitHub：<https://github.com/halolight/halolight-railway>

## 功能亮点

- **一键部署**：连接 GitHub 即可部署
- **自动检测**：Nixpacks 自动检测项目类型
- **托管数据库**：一键创建 PostgreSQL/MySQL/Redis
- **持久存储**：支持 Volume 挂载
- **Preview 环境**：PR 自动创建预览环境
- **免费额度**：每月 $5 免费额度

## 一键部署

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/halolight)

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/halolight/halolight-railway.git
cd halolight-railway

# 安装依赖
pnpm install

# 安装 Railway CLI
brew install railway

# 登录
railway login

# 本地开发
pnpm dev
```

## 部署到 Railway

### 方式一：Dashboard

1. 访问 [Railway Dashboard](https://railway.app/new)
2. 选择 "Deploy from GitHub repo"
3. 选择仓库，Railway 自动配置构建

### 方式二：CLI

```bash
# 初始化项目
railway init

# 连接到项目
railway link

# 部署
railway up
```

## Railway 配置

### railway.json

```json
{
  "$schema": "https://railway.app/railway.schema.json",
  "build": {
    "builder": "NIXPACKS"
  },
  "deploy": {
    "startCommand": "pnpm start",
    "healthcheckPath": "/api/health",
    "healthcheckTimeout": 300,
    "restartPolicyType": "ON_FAILURE"
  }
}
```

### 环境变量

```bash
# 通过 CLI 设置
railway variables set NEXT_PUBLIC_API_URL=/api
railway variables set DATABASE_URL=${{Postgres.DATABASE_URL}}
```

## 数据库集成

```bash
# 添加 PostgreSQL
railway add --plugin postgresql

# 添加 Redis
railway add --plugin redis

# 数据库 URL 自动注入为环境变量
```

## 域名配置

```bash
# 添加自定义域名
railway domain add halolight-railway.h7ml.cn
```

## 相关链接

- [HaloLight 文档](https://halolight.docs.h7ml.cn)
- [Railway 文档](https:/docs.railway.app/)
- [Railway Templates](https://railway.app/templates)

## 许可证

[MIT](LICENSE)
