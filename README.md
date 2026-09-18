### OTA-Service 推送服务

主要用于apk升级推送更新服务，主要属于服务端的搭建

docker run搭建方式

```bash
docker run -d \
  --name ota-server-container \
  --restart unless-stopped \
  -p 9608:9608 \
  -v ./firmware:/app/firmware \
  ota-service:1.1.3

```

docker compose部署方式



```bash
version: '3.8'

services:
  ota-service:
    image: ota-service:1.1.3
    container_name: ota-server-container
    restart: unless-stopped
    ports:
      - "9608:9608"
    volumes:
      - ./firmware:/app/firmware
```



当忘记密码或者重置密码请在容器内部删除或修改admin.json文件

部署之后访问https://ip+端口访问，并设置初始密码
<img width="1580" height="935" alt="image-20260918125143925" src="https://github.com/user-attachments/assets/fca89e97-cdd2-421b-9505-80154cc26b83" />



请求方式`/api/ota/check` 

直接下载的方式 `/api/ota/latest/download`

如需部署上的帮助请联系作者Fane 

Mail：otaservice@89798794.xyz
