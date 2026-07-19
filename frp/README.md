## 启动

```shell
cd ~/IdeaProjects/ricewines/home-deploy/frp
```

```shell
Get-Content D:\Users\CXH\data\secret\.env.secret.txt | ForEach-Object {$l=$_.Trim();if($l -and !$l.StartsWith("#")){$i=$l.IndexOf('=');$k=$l.Substring(0,$i).Trim();$v=$l.Substring($i+1).Trim();[Environment]::SetEnvironmentVariable($k,$v,"Process")}}
```

```shell
echo "FRPC_WEB_SERVER_PASSWORD=$env:FRPC_WEB_SERVER_PASSWORD";
echo "INVEST_VERSION=$env:INVEST_VERSION";
echo "QAZCXH_163_COM_MAIL_PASSWORD=$env:QAZCXH_163_COM_MAIL_PASSWORD";
echo "ZHI_PU_AI_API_KEY=$env:ZHI_PU_AI_API_KEY";
```

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