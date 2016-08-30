# vagrant
shadowsocks
shadowsocks-libev

介绍

Shadowsocks-libev是一个轻量级安全SOCKS5吗 代理为嵌入式设备和低端的盒子。

这是一个港口Shadowsocks由@clowwindy,这是由@madeye和@linusyang。

当前版本:2.5.0 |更新日志

特拉维斯置信区间:Travis CI

特性

Shadowsocks-libev是用纯C,只取决于libev和OpenSSL或mbedTLS或PolarSSL。

在正常使用,内存占用600 kb和CPU利用率 不超过5%的低端路由器(水牛WHR-G300N V2 400 mhz MIPS CPU, 32 mb内存和4 mb flash)。

功能的完整列表shadowsocks的不同版本之间的比较, 指的是Wiki页面。

安装

特定的指导

Debian & Ubuntu
从存储库安装
从源代码构建deb包
配置和启动该服务
Fedora & RHEL
从存储库安装
OpenSUSE
从存储库安装
从源代码构建
Archlinux
NixOS
女水妖
类unix系统上直接构建和安装
FreeBSD
OpenWRT
OS X
窗户
预构建配置指南

对于已经具备配置选项的完整列表, 试一试configure --help。

使用替代加密库

有三个加密库:

OpenSSL(默认的)
mbedTLS
PolarSSL(弃用)
mbedTLS

建立针对mbedTLS,指定--with-crypto-library=mbedtls和--with-mbedtls=/path/to/mbedtls运行时./configure。

Windows用户将需要额外的工作,当编译mbedTLS库, 看到这个问题对细节信息。

PolarSSL(弃用)

建立针对PolarSSL,指定--with-crypto-library=polarssl和--with-polarssl=/path/to/polarssl运行时./configure。

PolarSSL1.2.5或更新的是必需的。 目前,PolarSSL不支持 CAST5-CFB、DES-CFB IDEA-CFB,RC2-CFB SEED-CFB。
RC4由PolarSSL只支持1.3.0或以上。
使用共享库系统

请指定--enable-system-shared-lib。 这将取代捆绑libev,libsodium和libudns与相应的库安装 系统在编译和链接。

Debian & Ubuntu

从存储库安装

注意:存储库并不总是包含最新版本。 如果你想要最新版本请从源代码构建(见下文)

使用Debian的官方库不稳定:

sudo apt更新
sudo apt安装shadowsocks-libev
从源代码构建deb包

支持平台:

Debian 7(见下文),8,不稳定
Ubuntu 14.04(见下文),Ubuntu 14.04,15.04,15.10或更高版本
Ubuntu 14.04用户注意: 包建立在Ubuntu 14.04可以使用在以后的Ubuntu版本。 然而, 包基于Debian 7/8/9或Ubuntu 14.10 +不能被安装在 Ubuntu 14.04。

注意Debian 7。 x用户: 建立在Debian包7(老生常谈的),您需要启用debian-backports安装systemd-compatibility包dh-systemd或init-system-helpers。 请按照说明Debian补丁。

这也意味着你只能安装这些包建在系统init-system-helpers安装。

否则,试图直接从源代码构建和安装。 看到Linux下面的部分。

cdshadowsocks-libev
sudo apt-get安装——no-install-recommends建设重要autoconf libtool libssl-dev \
呆呆debhelper dh-systemd init-system-helpers pkg-config asciidoc xmlto apg
dpkg-buildpackage - b -美国加州大学-我cd. .
sudo dpkg - shadowsocks-libev*. deb
配置和启动该服务

# Edit the configuration file
sudo vim /etc/shadowsocks-libev/config.json

# Edit the default configuration for debian
sudo vim /etc/default/shadowsocks-libev

# Start the service
sudo /etc/init.d/shadowsocks-libev start    # for sysvinit, or
sudo systemctl start shadowsocks-libev      # for systemd
Fedora & RHEL

支持分布包括

Fedora 22日,23日,24日
RHEL 6、7和衍生品(包括科学Linux CentOS)
从存储库安装

使通过回购dnf:

su -c 'dnf copr enable librehat/shadowsocks'
或下载百胜回购Fedora Copr并把它在/etc/yum.repos.d/。 释放EpelRHEL及其衍生物。

然后,安装shadowsocks-libev通过dnf:

苏- c”dnf更新”苏- c”dnf安装shadowsocks-libev”
或yum:

苏- c”yum更新”苏- c”yum安装shadowsocks-libev”
OpenSUSE

从存储库安装

使用以下命令安装存储库。

sudo zypper安装shadowsocks-libev
从源代码构建

你应该安装zlib-devel和libopenssl-devel第一。

sudo zypper更新
sudo zypper安装zlib-devel libopenssl-devel
然后下载源代码包和编译。

git克隆https://github.com/shadowsocks/shadowsocks-libev.gitcdshadowsocks-libev
. / configure& &使
sudo make install
Archlinux

sudo pacman - s shadowsocks-libev
请参阅下游PKGBUILD脚本为额外的修改和特定错误。

NixOS

nix-env ia nixos.shadowsocks-libev
女水妖

nix-env ia nixpkgs.shadowsocks-libev
Linux

类unix系统,特别是Debian-based系统, 例如Ubuntu,Debian Linux Mint,您可以构建二进制是这样的:

sudo apt-get安装——no-install-recommends建设重要autoconf libtool libssl-dev asciidoc xmlto
. / configure& &使
sudo make install
FreeBSD

苏cd/usr/ports/net/shadowsocks-libev
制作安装
编辑你的配置。 json文件。 默认情况下,它是位于/usr/local/etc/shadowsocks-libev。

要启用shadowsocks-libev,添加以下rc /etc/rc.变量 配置文件:

shadowsocks_libev_enable="YES"
启动Shadowsocks服务器:

服务shadowsocks_libev开始
OpenWRT

请注意:你可能想使用openwrt-shadowsocks,这是专为OpenWRT开发。

#在OpenWRT构建根目录
pushd包
git克隆https://github.com/shadowsocks/shadowsocks-libev.gitpopd

#在网络启用shadowsocks-libev类别使menuconfig#可选让- j#构建包使V = 99包/ shadowsocks-libev / openwrt /编译
OS X

OS X的使用家酿安装或建立。

安装自制程序:

ruby - e”$(curl https://raw.githubusercontent.com/Homebrew/install/master/install -fsSL)”
安装shadowsocks-libev:

酿造安装shadowsocks-libev
窗户

对于Windows,使用MinGW(msys)或Cygwin。 目前,只有ss-local支持建立针对MinGW(msys)。

如果您使用的是MinGW(msys),请下载OpenSSL或PolarSSL源tarball msys的主目录,这样构建(可能需要几分钟):

OpenSSL

焦油zxf openssl-1.0.1e.tar.gzcdopenssl-1.0.1e
。 / config——prefix =”$ HOME/预先构建的”——openssldir =”$ HOME/预先构建的openssl”使& &制作安装
PolarSSL

焦油zxf polarssl-1.3.2-gpl.tgzcdpolarssl-1.3.2
使自由WINDOWS = 1
使安装DESTDIR =”$ HOME/预先构建的”
然后,使用下面的命令构建二进制文件,和所有.exe文件 将建在$HOME/ss/bin:

OpenSSL

。 /配置——prefix =”$ HOME/党卫军”——使用openssl =”$ HOME/预先构建的”使& &制作安装
PolarSSL

。 /配置——prefix =”$ HOME/党卫军”——with-crypto-library = polarssl with-polarssl =$ HOME/预先构建的
使& &制作安装
使用

详细和完整列表的所有支持的参数,你可以参考 分别手册页的应用程序。

    ss-[local|redir|server|tunnel]

       -s <server_host>           host name or ip address of your remote server

       -p <server_port>           port number of your remote server

       -l <local_port>            port number of your local server

       -k <password>              password of your remote server

       [-m <encrypt_method>]      encrypt method: table, rc4, rc4-md5,
                                  aes-128-cfb, aes-192-cfb, aes-256-cfb,
                                  bf-cfb, camellia-128-cfb, camellia-192-cfb,
                                  camellia-256-cfb, cast5-cfb, des-cfb, idea-cfb,
                                  rc2-cfb, seed-cfb, salsa20 ,chacha20 and
                                  chacha20-ietf

       [-f <pid_file>]            the file path to store pid

       [-t <timeout>]             socket timeout in seconds

       [-c <config_file>]         the path to config file

       [-i <interface>]           network interface to bind,
                                  not available in redir mode

       [-b <local_address>]       local address to bind,
                                  not available in server mode

       [-u]                       enable udprelay mode,
                                  TPROXY is required in redir mode

       [-U]                       enable UDP relay and disable TCP relay,
                                  not available in local mode

       [-A]                       enable onetime authentication

       [-L <addr>:<port>]         specify destination server address and port
                                  for local port forwarding,
                                  only available in tunnel mode

       [-d <addr>]                setup name servers for internal DNS resolver,
                                  only available in server mode

       [--fast-open]              enable TCP fast open,
                                  only available in local and server mode,
                                  with Linux kernel > 3.7.0

       [--acl <acl_file>]         config file of ACL (Access Control List)
                                  only available in local and server mode

       [--manager-address <addr>] UNIX domain socket address
                                  only available in server and manager mode

       [--executable <path>]      path to the executable of ss-server
                                  only available in manager mode

       [-v]                       verbose mode

notes:

    ss-redir provides a transparent proxy function and only works on the
    Linux platform with iptables.

高级用法

最新shadowsocks-libev提供了雨后储水区模式。 您可以配置您的基于linux的盒子或路由器代理所有TCP流量透明。

# Create new chain
root@Wrt:~# iptables -t nat -N SHADOWSOCKS
root@Wrt:~# iptables -t mangle -N SHADOWSOCKS

# Ignore your shadowsocks server's addresses
# It's very IMPORTANT, just be careful.
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 123.123.123.123 -j RETURN

# Ignore LANs and any other addresses you'd like to bypass the proxy
# See Wikipedia and RFC5735 for full list of reserved networks.
# See ashi009/bestroutetb for a highly optimized CHN route list.
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 0.0.0.0/8 -j RETURN
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 10.0.0.0/8 -j RETURN
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 127.0.0.0/8 -j RETURN
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 169.254.0.0/16 -j RETURN
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 172.16.0.0/12 -j RETURN
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 192.168.0.0/16 -j RETURN
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 224.0.0.0/4 -j RETURN
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -d 240.0.0.0/4 -j RETURN

# Anything else should be redirected to shadowsocks's local port
root@Wrt:~# iptables -t nat -A SHADOWSOCKS -p tcp -j REDIRECT --to-ports 12345

# Add any UDP rules
root@Wrt:~# ip route add local default dev lo table 100
root@Wrt:~# ip rule add fwmark 1 lookup 100
root@Wrt:~# iptables -t mangle -A SHADOWSOCKS -p udp --dport 53 -j TPROXY --on-port 12345 --tproxy-mark 0x01/0x01
root@Wrt:~# iptables -t mangle -A SHADOWSOCKS_MARK -p udp --dport 53 -j MARK --set-mark 1

# Apply the rules
root@Wrt:~# iptables -t nat -A OUTPUT -p tcp -j SHADOWSOCKS
root@Wrt:~# iptables -t mangle -A PREROUTING -j SHADOWSOCKS
root@Wrt:~# iptables -t mangle -A OUTPUT -j SHADOWSOCKS_MARK

# Start the shadowsocks-redir
root@Wrt:~# ss-redir -u -c /etc/config/shadowsocks.json -f /var/run/shadowsocks.pid
在KCP Shadowsocks

很容易使用shadowsocks和KCP在一起kcptun。

shadowsocks / KCP的目标是提供一个完全可配置的,基于UDP协议来改善贫穷的连接,如高丢包3 g网络。

设置您的服务器

server_linux_amd64 - l:21 - t 127.0.0.1:443——地下室没有mtu 1200——nocomp模式正常——dscp 46&ss-server - s 0.0.0.0 - p 443 - k passwd - m chacha20 - u
设置你的客户

client_linux_amd64 - l 127.0.0.1:1090 - r<server_ip>:21——地下室没有mtu 1200——nocomp模式正常——dscp 46&ss-local - s 127.0.0.1 - p 1090 - k passwd - m chacha20 - l 1080 - b 0.0.0.0&ss-local - s<server_ip>443 - p - k passwd - m chacha20 - l 1080 - u - b 0.0.0.0
安全提示

尽管shadowsocks-libev可以处理成千上万的并发连接好,我们仍然建议 设置服务器的防火墙规则来限制每个用户连接:

# Up to 32 connections are enough for normal usage
iptables -A INPUT -p tcp --syn --dport ${SHADOWSOCKS_PORT} -m connlimit --connlimit-above 32 -j REJECT --reject-with tcp-reset
许可证

版权(C)2016 Max Lvmax.c.lv@gmail.com

这个程序是自由软件:可以重新分配和/或修改 GNU通用公共许可证的条款下发布的 自由软件基金会,版本3的许可,或 (任您选)其后的版本。

这个程序是分布式的,希望这将是有用的, 但是没有任何保证;没有即使的默示保证 适销性或健身为特定目的。 看到 GNU通用公共许可证的更多细节。

你应该收到了GNU通用公共许可证的副本 以及这个项目。 如果没有,看http://www.gnu.org/licenses/。
