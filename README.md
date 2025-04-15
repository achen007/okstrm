# 🚀 OKStrm - 解决115网盘直链难题

基于 115 开放平台，使用一个 Docker 镜像即可实现网盘扫描、STRM 文件生成，并实时获取直链供媒体库调用。

## 🐳 快速部署

```bash
docker run -d \
  --name okstrm \
  -v /data/okstrm:/data \
  -p 9001:35001 \
  -e "STRM_IP=192.168.61.204" \  # 宿主机IP（必填）
  -e "STRM_PORT=9001" \         # 上面设置的本地端口，即9001（必填）
  --restart=always \
  nurdlewang/okstrm:1.0.4
```
### 📊 视频教程
[115网盘直链神器｜Docker秒生STRM](https://www.bilibili.com/video/BV1RGoWY3EYQ/?share_source=copy_web&vd_source=d5f838fa2ac59ef6506d03c784127ff8)


### ⚙️ 参数说明
| 参数 | 必填 | 默认值 | 说明 |
|------|------|--------|------|
| `STRM_IP` | 是 | 无 | 宿主机的IP地址 |
| `STRM_PORT` | 是 | 无 | 服务监听端口 |
| `/data` | 是 | 无 | strm文件存储路径 |

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
- 免费试用72小时
- 1年订阅 ￥9.9 
- 3年订阅 ￥19.9
- 🔑 订阅与115账号绑定
```
