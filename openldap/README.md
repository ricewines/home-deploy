## 拉取镜像

```shell
cd ~/IdeaProjects/ricewines/home-deploy/openldap/ ; docker compose pull
```

## 启动

```shell
docker compose up -d
```

## 停止

```shell
docker compose down
```

```shell
docker-compose config | findstr LDAP_ADMIN_PASSWORD
```