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

## 内部运行

```shell
ollama run qwen3.5:0.8b
```

## hello

```shell
curl.exe http://localhost:11434/api/chat -d '{\"model\":\"qwen3.5:0.8b\",\"messages\":[{\"role\":\"user\",\"content\":\"hi\"}],\"stream\":false}'
```

## 来源

[Ollama qwen3.5 模型库](https://ollama.com/library/qwen3.5)