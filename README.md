# caddy-dns

获取caddy最新版本并构建包含cloudflare dns插件的docker镜像

每日检查并构建，有amd64和arm64以及armv7三个架构的镜像版本

使用：
```
version: '3.9'
services:
  caddy:
    image: caddy-dns:latest
    container_name: caddy
    ports:
      - 80:80
      - 443:443
    environment:
      - CLOUDFLARE_API_TOKEN=[[cloudflare_token]]
    volumes:
      - ${HOME}/docker/caddy/Caddyfile:/etc/caddy/Caddyfile:ro
      - ${HOME}/docker/caddy/data:/data
      - ${HOME}/docker/caddy/config:/config
    restart: unless-stopped
```