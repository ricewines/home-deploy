## 环境

```shell
Get-Content D:\Users\CXH\data\secret\.env.secret.txt | ForEach-Object {$l=$_.Trim();if($l -and !$l.StartsWith("#")){$i=$l.IndexOf('=');$k=$l.Substring(0,$i).Trim();$v=$l.Substring($i+1).Trim();[Environment]::SetEnvironmentVariable($k,$v,"Process")}} ; 
echo "QAZCXH_163_COM_MAIL_PASSWORD=$env:QAZCXH_163_COM_MAIL_PASSWORD";
echo "ZHI_PU_AI_API_KEY=$env:ZHI_PU_AI_API_KEY";
echo "SPRING_PROFILES_ACTIVE=$env:SPRING_PROFILES_ACTIVE";
echo "INVEST_VERSION=$env:INVEST_VERSION";
```

```shell
; $env:PATH+=";"+$env:USERPROFILE+"\AppData\Roaming\JetBrains\IntelliJIdea2026.2\node\versions\24.18.1\" ;
# 校验npm版本
npm -v;
; $env:JAVA_HOME = "C:\Users\chixu\.jdks\openjdk-26.0.2" ; echo "已设置JAVA_HOME：$env:JAVA_HOME" ;
# 校验Java版本
& "$env:JAVA_HOME\bin\java.exe" -version ;
```

```shell
cd ~\IdeaProjects\ricewines\home-deploy\chixuehuidocker\invest-page
```

## 下载和解压工程accounting-page

```shell
npm pack accounting-page@$env:INVEST_VERSION ; mkdir $HOME\run\accounting-page\ ; tar -C $HOME\run\accounting-page\ -xzvf ./accounting-page-$env:INVEST_VERSION.tgz ; Remove-Item accounting-page-$env:INVEST_VERSION.tgz -Force;
# 部署工程accounting-page
cd $HOME\run\accounting-page\package ; npm install ; npm run build ;
```

## 下载和解压工程invest-admin-page

```shell
npm pack invest-admin-page@$env:INVEST_VERSION ; mkdir $HOME\run\invest-admin-page\ ; tar -C $HOME\run\invest-admin-page\ -xzvf ./invest-admin-page-$env:INVEST_VERSION.tgz ; Remove-Item invest-admin-page-$env:INVEST_VERSION.tgz -Force;
# 部署工程invest-admin-page
cd $HOME\run\invest-admin-page\package ; npm install ; npm run build;
```

```shell
cd ~/run ; Remove-Item -Recurse -Force invest ; git clone https://github.com/ricewines/invest.git ; cd invest
```

```shell
./mvnw clean install
```

## 拉取镜像

```shell
cd ~/IdeaProjects/ricewines/home-deploy/chixuehuidocker/invest-page/ ; docker compose pull ;docker compose down
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