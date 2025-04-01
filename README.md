# 关于本项目
基于115开放平台，无需安装任何额外的软件，实现一站式扫描、生成strm、获取直链 支持win mac

# 运行
解压之后双击运行，初次使用需要使用115手机客户端扫码授权。

会出现功能选项

1. 扫描网盘

2. 生成strm

3. 启动服务，注意影视库服务器不能挂全局代理

依次运行功能选项1、2、3，将第二步生成的strm正常刮削后放入媒体库软件即可。

# 配置项
strm_directory =

strm文件存储目录，空代表当前目录。 windows配置示例 C:\Users\Administrator\Downloads\strm_115 mac配置示例 /Volumes/Data/strm_115

remote_serv_ip = 127.0.0.1 remote_serv_port = 25002

转发服务的IP和监听端口，影视库需要能访问到。 必须一次配置好，后期更改影响转发，若更改需重新生成strm。 最好配置成本机可以被局域网访问的IP。127.0.0.1只能本机访问，如果媒体库在本机则无需修改。
