# 关于本项目
基于115开放平台，无需安装任何额外的软件，一个docker镜像实现网盘扫描、生成strm、获取直链

# docker部署


docker run -d \
--name okstrm \
--volume /data/okstrm:/data \
-p 9001:35001 \
-e "STRM_IP=192.168.61.204" \
-e "STRM_PORT=9001" \
--restart=always \
nurdlewang/okstrm:1.0.4

9001随便设置，映射到容器端口35001

STRM_IP是宿主机的IP，STRM_PORT是设置的宿主机的本地端口。

这两个参数必须设置，否则容器无法提供直链获取服务



# 运行

1. 部署完成后先扫描网盘同步数据

2. 同步数据后生成strm

3. 自行刮削使用即可


# 说明

免费测试三天，如果需要继续使用，选择购买，1年9.9，3年19.9


# 功能补充

有功能方面的建议可以提出
