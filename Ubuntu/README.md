# 使用[netboot](https://github.com/netbootxyz/netboot.xyz)安装 Oracle Cloud [Ubuntu 22.04]()系统

## 架构：[Arm64]()

先决条件：

1.arm64主机

2.ssh 连接到主机 （root 用户）

[查看最新版 netboot](https://github.com/netbootxyz/netboot.xyz)

## 1.在 SSH 终端执行以下命令：
```bash
apt update -y
apt install wget -y
cd /boot/efi/EFI
wget https://github.com/netbootxyz/netboot.xyz/releases/download/替换netboot最新版本号/netboot.xyz-arm64.efi
```
## 2.进入甲骨文控制台启动 Cloud Shell 连接 选择 `Boot Maintenance Manager`
<img src="" />

## 3.SSH终端执行`reboot`（或直接页面重新引导） ，并在 Cloud Shell 里面不停按键盘 ESC 键，进入 BIOS
<img src="" />

## 4.选择 Boot Maintenance Manager —> EFI —> netboot.xyz-arm64.efi，点击回车，进行引导
<img src="" />

## 5.选择 `Linux Network Installs (arm64)`
<img src="" />

## 6.选择 Ubuntu ---> Ubuntu 22.04 TLS jammy 回车 
<img src="" />

## 7.使用 ‘上下键’ 切换至 `Continue in rich mode` 回车
<img src="" />

## 8.Keyboard configuration 布局 (保持默认)
<img src="" />

## 9.Network connection 网络连接 (保持默认)
<img src="" />

## 10.Configur proxy 配置代理 (不用设置)
<img src="" />

## 11. Guided storage configuration 引导存储配置 保持默认
## 12.storage configuration 存储配置保持默认
## 13.此时将进行安装步骤的继续，‘上下键’切换至 `Continue` 回车
## 14.创建用户和密码
## 15.出现 upgrade to ubuntu pro （升级到 ubuntu 专业版）保持默认即可
## 16.此步骤很重要，‘上下键’切换到 [ ] Install OpenSSH server 使用 ‘空格键’ 将其选择；

### 17.安装完成，重启

# 必要的修改，（如不修改此项，在 SSH 终端切换到 root 用户时会多一步密码验证）
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
## 此时在切换 `root` 用户时无需密码验证。
