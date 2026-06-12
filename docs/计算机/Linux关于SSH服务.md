### 关于SSH服务

检查是否监听正确端口

```
sudo netstat -tlnp | grep :22
```

Linux 检查 SSH 服务

```
sudo systemctl status ssh                     
○ ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: disabled)
     Active: inactive (dead)
       Docs: man:sshd(8)
             man:sshd_config(5)
```

SSH 服务没有启动，而且被禁用

### **1. 启动 SSH 服务**

```
# 启动 SSH 服务（立即生效）
sudo systemctl start ssh

# 或者使用服务全名（有些系统是 sshd）
sudo systemctl start sshd
```

### **2. 设置开机自启**

```
# 启用开机自动启动
sudo systemctl enable ssh

# 如果上面不行，尝试
sudo systemctl enable sshd
```

开启ssh，putty即可连通，如还不行，再看看是不是Windows这边防火墙的问题

---



### Ubuntu：

**在 Ubuntu 中配置 SSH 服务：**

1、打开终端‌（快捷键 Ctrl + Alt + T）
2、检查是否已安装 OpenSSH Server‌：
ssh localhost
若提示 Connection refused，说明未安装

3、安装 OpenSSH Server‌：
sudo apt update
sudo apt install openssh-server

4、‌启动 SSH 服务‌：
sudo systemctl start ssh

5、设置开机自启‌（推荐）：
sudo systemctl enable ssh

6、验证 SSH 是否运行‌：
ps -e | grep sshd
若输出包含 sshd，表示服务已启动

⚠️ 注意：部分 Ubuntu 版本默认禁用 root 登录。如需 root 登录，需编辑 `/etc/ssh/sshd_config`，将 `PermitRootLogin` 改为 `yes`，并重启 SSH 服务
