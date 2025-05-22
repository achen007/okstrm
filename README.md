# 🚀 OKStrm - 解决115网盘直链难题

基于 115 开放平台，使用一个 Docker 镜像即可实现网盘扫描、STRM 文件生成，并实时获取直链供媒体库调用。

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
  nurdlewang/okstrm:1.0.16
```

### ✅ 方法二：使用 docker-compose

```bash
version: '3.8'

services:
  okstrm:
    container_name: okstrm
    image: nurdlewang/okstrm:1.0.16
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


## 📋 使用指南



### 1. 初始化扫描
```bash
选择1进行网盘扫描，选择1会先返回网盘根目录，自行选择目录进行扫描
```

### 2. 生成STRM
```bash
扫描完成后选择2或者3生成strm文件，2是增量生成，3是全量生成
```
### 3. 媒体库使用
```bash
自行刮削生成的strm文件，刮削完成放入媒体库，媒体库与okstrm网络通即可
```


## ⚠️ 常见问题

1. **有的emby版本播放strm会出现无法拖动、找不到流的情况**
   - 更换其他版本
   

## 📜 订阅
```markdown
- 免费试用7天
- 1年订阅 ￥9.9 
- 3年订阅 ￥19.9
- 🔑 订阅与115账号绑定
```

## 交流群
```markdown
- 建了个群，有部署问题和功能建议，可以一起交流。814050084
```


# 更新日志
## v1.0.16 - 2025-05-22
## v1.0.15 - 2025-05-21
## v1.0.14 - 2025-05-21
## v1.0.13 - 2025-05-21
## v1.0.12 - 2025-05-20
## v1.0.11 - 2025-05-07
## v1.0.10 - 2025-05-07
## v1.0.9 - 2025-04-30
## v1.0.8 - 2025-04-24
## v1.0.7 - 2025-04-21
## v1.0.6 - 2025-04-17
## v1.0.5 - 2025-04-15

### ✨ 新增
• 初始版本发布：包括基本的功能与后台界面



