## 拉取镜像

```shell
cd ~/IdeaProjects/ricewines/home-deploy/ai/ ; docker compose pull
```

## 启动

```shell
docker compose up -d
```

## 停止

```shell
docker compose down
```

## hello

```shell
curl.exe http://localhost:11434/api/chat -d '{\"model\":\"qwen3.5:0.8b\",\"messages\":[{\"role\":\"user\",\"content\":\"hi\"}],\"stream\":false}'
```