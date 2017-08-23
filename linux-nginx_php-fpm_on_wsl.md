# [Linux] WSL(Windows Subsystem Linux) 下 nginx + php-fpm 配置及常见问题

## 0. nginx 无法使用80端口
在 Windows 命令提示符中运行
```bat
netstat -ano
```
查看本地占用80端口的 PID, 看看占用的是哪个, 有人说是 Skype 的自动更新占用了80端口, 但是我卸载了 80 端口还是无效. 追查之后, 发现是 Windows 启动了自己的一个 www 服务, 名字叫做 `World Wide Web 发布服务`, 停用该服务即可.

## 1. http 访问 php 脚本超级慢(60s)
WSL 对 unix sock 支持不完善导致的, 将 php 代理由 unix sock 换成代理端口
```ini
fastcgi_pass 127.0.0.1:9000;
#fastcgi_pass unix:/run/php/php7.0-fpm.sock;
```