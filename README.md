# 使用说明

1. 生成证书
```
mkdir conf
openssl req -new -newkey rsa:4096 -days 365 -subj "/CN=localhost" \
        -nodes -x509 -keyout conf/auth.key -out conf/auth.cert
```

2. 需要修改 conf/registry-srv.yml 中的 realm 值，改为需要拉取镜像的主机可以访问的地址

3. 初始用户名/密码为 admin/admin

4. 在 /etc/docker/daemon.json 添加如下配置，使得推拉镜像时可以使用 http 协议，而不是强制使用 https 协议
```
{
    "insecure-registries": ["192.168.0.100:5000"]
}
```
地址根据自己的服务器设置
