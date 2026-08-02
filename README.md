# 🚀 okStrm - 解决115网盘直链难题

基于 115 开放平台，使用一个 Docker 镜像即可实现网盘扫描、STRM 文件生成，并实时获取直链供媒体库调用。

## 📋 使用文档
https://docs.qq.com/aio/DZXhwTVZETGtUYVpQ?p=9QcfFmIAIFgG8F4G8E3cRJ

## 🐳 快速部署

### ✅ 方法一：使用 docker run
```bash
docker run -d \
  --name okstrm \
  -v /data/okstrm:/data \
  -p 35001:35001 \   # okstrm服务接口（必填）
  -p 35002:35002 \   # 反代emby的接口（选填）
  -p 35003:35003 \   # 反代jellyfin的接口（选填）
  --restart=always \
  nurdlewang/okstrm:1.0.41
```

### ✅ 方法二：使用 docker-compose

```bash
version: '3.8'

services:
  okstrm:
    container_name: okstrm
    image: nurdlewang/okstrm:1.0.41
    restart: always
    ports:
      - "35001:35001"
      - "35002:35002"
      - "35003:35003"
    volumes:
      - /volume1/docker/okstrm:/data
    environment:
      - TZ=Asia/Shanghai
      - PYTHONUNBUFFERED=1
      - PYTHONIOENCODING=utf-8
```



### 📊 视频教程（B站）
[115网盘直链神器｜Docker秒生STRM](https://www.bilibili.com/video/BV1RGoWY3EYQ/?share_source=copy_web&vd_source=d5f838fa2ac59ef6506d03c784127ff8)


### ⚙️ 参数说明
| 参数 | 必填 | 默认值 | 说明 |
|------|------|--------|------|
| `/data` | 是 | 无 | config和strm文件存储路径 |

1. **在云上部署okstrm，如何生成https的直链？**
   - okstrm并不直接支持，如果用nginx反代okstrm并配置了https域名。可以通过 STRM_TYPE指定https或是http，STRM_IP指定域名，STRM_PORT指定端口

2. **okstrm运行缓存存储于/data/config/cache.db，如果发生迁移、重新部署、升级等情况，可直接迁移cache.db到相应位置**

3. **登录后前往【左边栏-设置】进行strm_ip和strm_port的设置，这两个参数就是网页地址栏里的IP和端口**


| 容器内部端口 | 必填 | 说明 |
|------|------|------|
| `35001` | 是 | okstrm服务端口  |
| `35002` | 否 | 反代emby的端口 |
| `35003` | 否 | 反代jellyfin的端口 |


