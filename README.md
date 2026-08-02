# Home Deploy

这是一个面向家庭/个人服务器环境的部署仓库，主要用于统一管理与 Ricewines / Seenings 相关的容器化服务、前端页面部署与反向代理配置。

## 1. 仓库用途

当前目录下收纳了多类服务配置，目标是把以下内容集中管理：

- 前端页面的容器化部署
- 反向代理与内网穿透
- LDAP 认证服务
- 文件管理服务
- 统一的 Docker 网络与环境变量配置

## 2. 目录说明

```text
home-deploy/
├── chixuehuidocker/
│   ├── invest-page/
│   └── seen-page/
├── frp/
├── openldap/
├── openlist/
├── LICENSE
└── README.md
```

### 2.1 chixuehuidocker

该目录用于部署与业务页面相关的容器环境，主要包含两套页面部署配置：

- invest-page：用于部署 Invest 相关页面，包含 Docker Compose、Nginx 配置和说明文档。
- seen-page：用于部署 Seen 相关页面，包含 Docker Compose、Nginx 配置和说明文档。

这两套配置都依赖一个共享的 Docker 网络，并且在部署前通常会准备好相关环境变量与构建依赖。

### 2.2 frp

用于部署 FRP 客户端服务，便于通过内网穿透把本地服务暴露到外部网络。当前配置中使用了 `frpc` 容器，并通过 Docker Compose 管理启动。

### 2.3 openldap

用于部署 LDAP 服务与 phpLDAPadmin 管理界面，适合用于统一身份认证或内部服务接入。

### 2.4 openlist

用于部署 OpenList 文件管理服务，适合提供一个可访问的文件列表/管理入口。

## 3. 通用前提

在启动这些服务前，建议确认以下内容：

- Docker 与 Docker Compose 已安装并可用
- 已创建共享网络：

```powershell
docker network create shared
```

- 部分服务依赖外部密钥文件，例如：

```text
D:\Users\CXH\data\secret\.env.secret.txt
```

该文件会被 Docker Compose 读取，用于注入环境变量。

## 4. 常用操作

### 4.1 启动服务

每个子目录都提供了自己的启动方式，常见命令如下：

```powershell
cd .\frp
docker compose up -d
```

```powershell
cd .\openldap
docker compose up -d
```

```powershell
cd .\openlist
docker compose up -d
```

```powershell
cd .\chixuehuidocker\invest-page
docker compose pull
docker compose up -d
```

```powershell
cd .\chixuehuidocker\seen-page
docker compose pull
docker compose up -d
```

### 4.2 停止服务

```powershell
docker compose down
```

### 4.3 拉取镜像

```powershell
docker compose pull
```

## 5. 各服务的简要说明

### 5.1 Invest 页面部署

位于 [chixuehuidocker/invest-page](chixuehuidocker/invest-page) 下，主要用于部署 Invest 相关页面。配置文件中包含：

- Docker Compose 定义
- Nginx 配置
- 页面构建相关说明

部署时通常会先准备前端包并进行构建，再由容器进行服务发布。

### 5.2 Seen 页面部署

位于 [chixuehuidocker/seen-page](chixuehuidocker/seen-page) 下，主要用于部署 Seen 相关页面。其流程与 Invest 页面部署相似，包含：

- 页面构建与打包
- 容器镜像拉取
- Docker 服务启动

### 5.3 FRP

位于 [frp](frp) 下，提供内网穿透能力，适合把本地服务暴露给外部访问。

### 5.4 OpenLDAP

位于 [openldap](openldap) 下，提供 LDAP 目录服务与 Web 管理界面，常用于统一认证和用户目录管理。

### 5.5 OpenList

位于 [openlist](openlist) 下，提供一个文件管理与访问入口，适合做私有文件共享或资源索引服务。

## 6. 备注

- 该仓库本身更偏向“部署脚本和配置集合”，并不包含完整业务代码。
- 具体的前端构建步骤、环境变量和服务端口信息，请以各子目录下的 README 与 Compose 配置为准。
- 如果需要进一步扩展，建议继续把各服务的依赖、端口和默认账号信息整理到独立文档中，便于长期维护。
