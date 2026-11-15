## 下载

```shell
cd ~/IdeaProjects/ricewines/home-deploy/frp
```

```shell
curl.exe --ssl-no-revoke -O https://github.com/fatedier/frp/releases/download/v0.72.0/frp_0.72.0_linux_amd64.tar.gz
```

## 启动
```shell
docker network create shared
```

```shell
docker compose up -d
```

## 停止

```shell
docker compose down
```