# 创意节微信小程序

## 项目概述

创意节微信小程序是一个专为创意节活动设计的平台，主要面向粤港澳大湾区大学生创意节等创意比赛活动。该小程序提供比赛信息浏览、团队组建、消息通知和个人中心等功能，旨在为参与创意节活动的用户提供便捷的信息获取和团队协作体验。

## 功能特点

### 首页（灵感学院）
- 轮播图展示热门比赛和活动
- 搜索功能，支持查找比赛/活动/企业
- 热门赛事展示和分类浏览
- 通知提醒功能

### 团队管理
- 我的队伍信息展示
- 支持单位和合作单位展示
- 团队成员管理
- 团队项目协作

### 消息中心
- 系统通知
- 比赛更新提醒
- 团队消息

### 个人中心
- 用户信息管理
- 参赛记录
- 个人设置

## 技术栈

- 框架：uni-app (Vue 3 + TypeScript)
- 编译工具：Vite
- 小程序平台：微信小程序
- UI组件：自定义组件

## 安装和运行

### 环境要求
- Node.js (推荐使用最新LTS版本)
- 微信开发者工具

### 安装步骤

1. 克隆项目到本地
```bash
git clone [仓库地址]
cd wx-miniprogram-creative-festival
```

2. 安装依赖
```bash
npm install
```

3. 开发模式运行（微信小程序）
```bash
npm run dev:mp-weixin
```

4. 使用微信开发者工具打开项目目录下的`dist/dev/mp-weixin`文件夹

### 构建生产版本
```bash
npm run build:mp-weixin
```

## 项目结构

```
├── src                     # 源代码目录
│   ├── pages               # 页面文件
│   │   ├── index           # 首页（灵感学院）
│   │   ├── team            # 团队页面
│   │   ├── message         # 消息中心
│   │   ├── profile         # 个人中心
│   │   └── admin           # 管理页面
│   ├── static              # 静态资源
│   │   ├── icons           # 图标文件
│   │   ├── images          # 图片资源
│   │   └── logo.png        # 应用logo
│   ├── App.vue             # 应用入口组件
│   ├── main.ts             # 应用入口文件
│   ├── manifest.json       # 应用配置文件
│   ├── pages.json          # 页面路由配置
│   └── uni.scss            # 全局样式文件
├── index.html              # HTML模板
├── package.json            # 项目依赖配置
├── tsconfig.json           # TypeScript配置
└── vite.config.ts          # Vite配置文件
```

## 开发指南

### 页面开发
新增页面需要在`src/pages.json`中添加对应的路由配置。

### 样式指南
项目使用`uni.scss`进行全局样式管理，建议遵循项目现有的样式规范。

### 小程序配置
小程序相关配置在`src/manifest.json`文件中，发布前需要填写正确的AppID。

## 贡献指南

1. Fork 项目仓库
2. 创建您的特性分支 (`git checkout -b feature/amazing-feature`)
3. 提交您的更改 (`git commit -m 'Add some amazing feature'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 打开一个 Pull Request

## 版本历史

- 0.0.0: 初始版本

## 许可证

[待定] - 请联系项目维护者获取许可信息

## 联系方式

项目维护者：[待补充]

---

© 2024 创意节微信小程序团队. 保留所有权利。