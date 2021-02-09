# W2ray

一键部署CDN+Websocket+SSL伪装的V2ray

基于Docker、Caddy和V2ray

## 服务器和域名解析

服务器系统推荐debian或ubuntu

域名解析时选择使用代理，实现CDN访问，推荐使用cloudflare

使用的域名即为后面的HOSTNAME

## 安装 Docker

一键安装docker
```bash
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
```

配置用户权限（重新登录生效）
```bash
$ sudo usermod -aG docker your-user
```

查看docker版本
```bash
$ docker --version
```

一键安装docker-compose
```bash
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```

查看docker-compose版本
```bash
$ docker-compose --version
```

## 下载W2ray并配置

下载W2ray
```
$ git clone https://github.com/0xHJK/W2ray.git
```

修改`caddy/Caddyfile`：
- 修改域名
- 修改邮箱（随便写，用于证书注册）
- 修改密码（随便写，用于伪装）

修改`v2ray/config.json`：
- 修改uuid（使用uuidgen随机生成）

如果你用的是debian系统，可以使用`init-debian.sh`脚本自动修改

## 运行

阻塞模式（测试）
```bash
$ docker-compose up
```

后台运行
```bash
$ docker-compose up -d
```

访问 https://HOSTNAME 显示It works!则表示部署成功

## 本地配置

以V2rayU为例，默认配置如下

* address、host、tls servername 处填写 HOSTNAME
* id 处填写 UUID
* security 选择 aes-128-gcm
* network 选择 ws
* path 填写 /ray

⚠️ 如果修改了配置文件，则服务端和客户端保持一致即可
