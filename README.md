# Parse-Server

`parse-server` 快速部署，假设本地已经配置好 `docker` 和 `docker-compose`。

修改 .env 文件，如下所示，其中 localhost 修改为本地 IP 地址。

```ini
BASE_URL=http://localhost
SOFTWARE_VERSION_TAG=latest
ADMIN_USERNAME=admin
ADMIN_PASSWORD=admin@123
ADMIN_EMAIL=admin@admin.com
PARSE_SERVER_APPLICATION_ID=admin-app-id
MASTER_KEY=admin-master-key
REST_KEY=rest-key
APP_NAME=MyApp
```

然后执行 `docker-compose up -d` 即可，然后打开 `http://{ip}:4040/apps/MyApp/browser/`，新增一个Class为 `person`。

执行命令，新增一条数据，并查看数据是否新增成功。

```shell
curl -X POST \
-H "X-Parse-Application-Id: admin-app-id" \
-H "X-Parse-REST-API-Key: rest-key" \
-H "Content-Type: application/json" \
-d '{"score":1337,"playerName":"Sean Plott","cheatMode":false}' \
http://localhost:1337/parse/classes/person

{"objectId":"7amBIuzAZW","createdAt":"2024-07-23T08:36:15.074Z"}
```
