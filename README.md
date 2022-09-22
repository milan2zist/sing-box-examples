## sing-box安装指南

- 下载 [sing-box](https://github.com/SagerNet/sing-box/releases)
- 程序 `/root/sing-box`
- 配置 `/root/sing-box_config.json`
- 证书 `/root/fullchain.cer`
- 私钥 `/root/private.key`
- systemctl文件 `/etc/systemd/system/sing-box.service`


```
chmod +x /root/sing-box
```

```
systemctl daemon-reload && systemctl enable sing-box
```

```
systemctl start sing-box
```

```
systemctl status sing-box
```

官方文档 [https://sing-box.sagernet.org](https://sing-box.sagernet.org/zh/configuration/)