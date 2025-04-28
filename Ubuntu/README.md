# 使用[netboot](https://github.com/netbootxyz/netboot.xyz)安装 Oracle Cloud [Ubuntu 22.04]()系统

## 架构：[Arm64]()

先决条件：

1. arm64 主机

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
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/2.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/3.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/4.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/5.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/6.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/7.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/8.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/9.png" />

2. 注意这一步需要选择 `Continue in basic mode >`，如果选择 `Continue in rich mode`会出现乱码！（默认配置，如图：）;
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/10.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/11.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/12.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/13.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/14.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/15.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/16.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/17.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/18.png" />
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/19.png" />

3. 到这一步需要根据自己需求设置用户名和密码；（如图所示）;
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/20.png" />

4. 默认配置并选择 `Continue`
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/21.png" />

5. 这一步需要（空格键）勾选 `Install OpenSSH server`;
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/22.png" />

6. 这一步保持默认，回车后等待片刻控制台会出现 `reboot` 字样;
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/23.png" />

7. 此时选择 `reboot` 重启服务器，当控制台出现 Login 表示系统安装完成，通过 WinSCP 或 Xshell 既可连接.
   <img src="https://github.com/Skyler-May/OracleCloud-ReSystem/blob/main/Ubuntu/img/24.png" />

# 必要的修改，（如不修改此项，在 SSH 终端切换到 root 用户时会多一步密码验证）

1. 打开终端并输入以下命令以编辑 sudoers 文件：

```bash
sudo visudo
```

2. 在打开的文件中找到这一行：`%sudo   ALL=(ALL:ALL) ALL` 在下面添加一行来允许特定用户在使用 sudo 时不需要输入密码。比如，假设你的用户名是 ubuntu：

```bash
ubuntu   ALL=(ALL) NOPASSWD: ALL
```

3. `Ctrl + x` 输入 `y` 回车

```bash
sudo -k
sudo -i
```

此时在切换 `root` 用户时无需密码验证。
