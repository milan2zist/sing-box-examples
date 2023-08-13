# [sing-box](https://github.com/SagerNet/sing-box) installation guide

## Server

### 安装

1. download program（**linux-amd64**）

```
curl -Lo /root/sing-box.tar.gz https://github.com/SagerNet/sing-box/releases/download/v1.3.6/sing-box-1.3.6-linux-amd64.tar.gz && tar -xzf /root/sing-box.tar.gz && cp -f /root/sing-box-*/sing-box /root && rm -r /root/sing-box.tar.gz /root/sing-box-* && chown root:root /root/sing-box && chmod +x /root/sing-box && mv -f /root/sing-box /usr/local/bin
```

- [compile program](https://github.com/chika0801/sing-box-examples/blob/main/compile_sing-box.md)

2. upload configuration 、certificate and private key


- 将配置文件改名为 **sing-box_config.json**，将证书文件改名为 **fullchain.cer**，将私钥文件改名为 **private.key**，将它们上传到 **/root** 目录

3. 下载systemctl配置

```
curl -Lo /etc/systemd/system/sing-box.service https://raw.githubusercontent.com/chika0801/sing-box-examples/main/sing-box.service && systemctl daemon-reload
```

4. 启动程序

```
systemctl enable --now sing-box
```

| 项目 | |
| :--- | :--- |
| 程序 | **/usr/local/bin/sing-box** |
| 配置 | **/root/sing-box_config.json** |
| 检查 | `sing-box check -c sing-box_config.json` |
| 重启 | `systemctl restart sing-box` |
| 状态 | `systemctl status sing-box` |
| 查看日志 | `journalctl -u sing-box -o cat -e` |
| 实时日志 | `journalctl -u sing-box -o cat -f` |

### 卸载

```
systemctl disable --now sing-box && rm -f /usr/local/bin/sing-box /root/sing-box_config.json /etc/systemd/system/sing-box.service
```

## 客户端

### Android 使用方法：

1. 下载Android客户端程序[SFA-arm64-v8a.apk](https://github.com/SagerNet/sing-box/releases)。
3. 参考[客户端配置](https://github.com/chika0801/sing-box-examples/blob/main/Tun/config_client_android.json)示例，按需修改后导入。

### Windows 使用方法：

1. 下载Windows客户端程序[sing-box-windows-amd64.zip](https://github.com/SagerNet/sing-box/releases)。
2. 新建一个批处理文件，内容为 `start /min sing-box.exe run`。
3. 参考[客户端配置](https://github.com/chika0801/sing-box-examples/blob/main/Tun/config_client_windows.json)示例，按需修改后将文件名改为 **config.json**，与 **sing-box.exe**，批处理文件放在同一文件夹里。
4. 右键点击 **sing-box.exe** 选择属性，选择兼容性，选择以管理员身份运行此程序，确定。
5. 运行批处理文件，在弹出的用户账户控制对话框中，选择是。
