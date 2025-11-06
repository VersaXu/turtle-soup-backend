# 🐢 海龟汤问答游戏后端

![后端服务](https://img.shields.io/badge/后端-API服务-blue)
![Node.js](https://img.shields.io/badge/Node.js-Express-green)
![Vercel](https://img.shields.io/badge/部署-Vercel-black)

## 项目介绍

这是海龟汤问答游戏的后端API服务，为前端游戏提供问答处理、谜题生成和用户认证功能。该服务使用Express.js构建，并部署在Vercel平台上。

### API服务

[API服务地址](https://turtle-soup-backend-hsry.vercel.app/)

## 功能特点

- 通义千问API集成，提供智能问答服务
- 谜题生成和管理
- 用户认证（简化版）
- CORS配置，支持前端跨域请求
- Vercel无服务器部署

## 技术架构

- **后端框架**：Express.js
- **运行环境**：Node.js
- **API集成**：阿里云通义千问
- **部署平台**：Vercel
- **前端通信**：CORS支持

## API端点

### 健康检查
- `GET /` - 返回服务状态信息

### 聊天API
- `POST /api/qwen/chat` - 与通义千问模型交互
  - 请求体: `{ "prompt": "用户输入的问题" }`
  - 返回: `{ "result": "AI回答内容" }`

### 认证API
- `POST /api/auth/login` - 用户登录
  - 请求体: `{ "username": "用户名", "password": "密码" }`
  - 返回: 包含访问令牌的用户信息

- `POST /api/auth/register` - 用户注册
  - 请求体: `{ "username": "用户名", "password": "密码" }`
  - 返回: 包含访问令牌的用户信息

## 本地开发

### 前置条件

- Node.js 14.x 或更高版本
- npm 或 yarn
- 通义千问API密钥（可选）

### 安装步骤

1. 克隆仓库
```bash
git clone https://github.com/VersaXu/turtle-soup-backend.git
cd turtle-soup-backend
```

2. 安装依赖
```bash
npm install
# 或
yarn install
```

3. 创建环境变量文件
```bash
echo "QWEN_API_KEY=your_api_key_here" > .env
```

4. 启动开发服务器
```bash
npm start
# 或
yarn start
```

服务将在 http://localhost:3000 运行。

## 项目结构

```
/
├── turtle-soup-server.js  # 主服务器文件
├── package.json          # 项目依赖
├── vercel.json           # Vercel部署配置
└── .env                  # 环境变量（本地开发用）
```

## 部署

项目配置为在Vercel上自动部署。当代码推送到主分支时，Vercel会自动构建并部署新版本。

### 部署步骤

1. 在Vercel上创建新项目
2. 连接GitHub仓库
3. 配置环境变量：
   - `QWEN_API_KEY`: 通义千问API密钥
   - `QWEN_BASE_URL`: API基础URL（可选）
   - `QWEN_MODEL`: 使用的模型（可选）
4. 部署项目

## 配置

### 环境变量

- `QWEN_API_KEY`: 通义千问API密钥
- `QWEN_BASE_URL`: 通义千问API基础URL
- `QWEN_MODEL`: 使用的模型名称
- `PORT`: 本地开发服务器端口

### Vercel配置

vercel.json文件包含Vercel部署所需的配置：

```json
{
  "version": 2,
  "builds": [
    {
      "src": "turtle-soup-server.js",
      "use": "@vercel/node"
    }
  ],
  "rewrites": [
    { "source": "/api/(.*)", "destination": "/turtle-soup-server.js" }
  ]
}
```

## 前端集成

前端项目通过环境变量配置API地址：

```
VITE_API_BASE_URL=https://turtle-soup-backend-hsry.vercel.app/api
```

## 贡献指南

欢迎为项目做出贡献！您可以通过以下方式参与：

1. 提交问题或建议
2. 提交代码改进
3. 增强AI问答功能

## 许可证

[MIT](LICENSE)

## 鸣谢

- 阿里云通义千问团队
- Express.js社区
- Vercel平台
- 项目贡献者