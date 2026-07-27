## 环境

```shell
Get-Content D:\Users\CXH\data\secret\.env.secret.txt | ForEach-Object {$l=$_.Trim();if($l -and !$l.StartsWith("#")){$i=$l.IndexOf('=');$k=$l.Substring(0,$i).Trim();$v=$l.Substring($i+1).Trim();[Environment]::SetEnvironmentVariable($k,$v,"Process")}}
```

```shell
echo "FRPC_WEB_SERVER_PASSWORD=$env:FRPC_WEB_SERVER_PASSWORD";
echo "SEEN_VERSION=$env:SEEN_VERSION";
echo "QAZCXH_163_COM_MAIL_PASSWORD=$env:QAZCXH_163_COM_MAIL_PASSWORD";
echo "ZHI_PU_AI_API_KEY=$env:ZHI_PU_AI_API_KEY";
```

```shell
$ $env:PATH+=";"+$env:USERPROFILE+"\AppData\Roaming\JetBrains\IntelliJIdea2026.2\node\versions\24.16.0\" ; cd ~\IdeaProjects\ricewines\home-deploy\chixuehuidocker\seen-page ; npm -v;
```

```shell
$$Env:JAVA_HOME = "C:\Users\chixu\.jdks\openjdk-26.0.1" ; echo "已设置JAVA_HOME：$Env:JAVA_HOME" ; java -version
```

## 下载和解压工程seen-font-end

```shell
npm pack seen-font-end@$env:SEEN_VERSION ; mkdir $HOME\run\seen-font-end\ ; tar -C $HOME\run\seen-font-end\ -xzvf ./seen-font-end-$env:SEEN_VERSION.tgz ; Remove-Item seen-font-end-$env:SEEN_VERSION.tgz -Force
```

## 部署工程seen-font-end

```shell
cd $HOME\run\seen-font-end\package ; npm install ; npm run build
```

```shell
cd ~/run ; Remove-Item -Recurse -Force seen-backend ; git clone https://github.com/seenings/seen-backend.git 
```

```shell
cd ~/run/seen-backend
```

```shell
./mvnw.cmd clean install
```

## 拉取镜像

```shell
cd ~/IdeaProjects/ricewines/home-deploy/chixuehuidocker/seen-page/ ; docker compose pull
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