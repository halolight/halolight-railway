# CLAUDE.md

This file provides guidance to Claude Code when working with this repository.

## 项目概述

HaloLight Railway 一键部署版本，零配置部署，支持托管数据库。

## 技术栈

- **框架**: Next.js 15 + React 19 + TypeScript
- **样式**: Tailwind CSS 4、shadcn/ui
- **部署**: Railway (Nixpacks)
- **数据库**: Railway PostgreSQL/MySQL/Redis

## 常用命令

```bash
pnpm dev          # 本地开发
pnpm build        # 生产构建
railway up        # 部署到 Railway
railway logs      # 查看日志
railway shell     # 进入容器
```

## Railway 特性

### Nixpacks 自动检测

Railway 使用 Nixpacks 自动检测：
- Node.js 版本 (从 package.json engines)
- 包管理器 (npm/yarn/pnpm)
- 构建命令和启动命令

### 服务引用

在环境变量中引用其他服务：
```
DATABASE_URL=${{Postgres.DATABASE_URL}}
REDIS_URL=${{Redis.REDIS_URL}}
```

### Preview 环境

每个 PR 自动创建独立预览环境，包含独立数据库。

## 环境变量

通过 Railway Dashboard 或 CLI 配置：
```bash
railway variables set KEY=value
railway variables
```
