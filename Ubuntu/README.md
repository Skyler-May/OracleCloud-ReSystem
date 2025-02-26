# 使用[netboot](https://github.com/netbootxyz/netboot.xyz)安装 Oracle Cloud [Ubuntu 22.04]()系统

## 架构：[Arm64]()

先决条件：

1. arm64主机

2. ssh 连接到主机 （root 用户）

3. [查看最新版 netboot](https://github.com/netbootxyz/netboot.xyz)

# SSH 终端执行以下命令：
```bash
apt update -y
apt install wget -y
cd /boot/efi/EFI
wget https://github.com/netbootxyz/netboot.xyz/releases/download/替换netboot最新版本号/netboot.xyz-arm64.efi
```
1. 重启主机，进入 BIOS，按 `ESC` 键进入引导菜单，选择 `Boot Maintenance Manager`;
<img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/1.png" />


<!-- # 必要的修改，（如不修改此项，在 SSH 终端切换到 root 用户时会多一步密码验证）
## 1.打开终端并输入以下命令以编辑sudoers文件：
```bash
sudo visudo
```
## 2.在打开的文件中找到这一行：
```bash
%sudo   ALL=(ALL:ALL) ALL
```
## 3.在这一行下面添加一行来允许特定用户在使用sudo时不需要输入密码。比如，假设你的用户名是ubuntu：
```bash
ubuntu   ALL=(ALL) NOPASSWD: ALL
```
## 4.`Ctrl + x` 输入 `y` 回车
```bash
sudo -k
sudo -i
```
## 此时在切换 `root` 用户时无需密码验证。 -->
