OpenWrt-dist
============

Provides some OpenWrt/LEDE packages

OpenWrt-dist is a depot of OpenWrt/LEDE device.

For more details, [check here](https://sourceforge.net/projects/openwrt-dist/).

## Install

### Form Sources

First, add openwrt-dist.pub file into opkg’s keys:

```bash
wget https://easypi.github.io/openwrt-dist/openwrt-dist.pub
opkg-key add openwrt-dist.pub
```

You can use the following command to get architecture:

```bash
opkg print-architecture | awk '{print $2}'
```

Then, add the following line to `/etc/opkg/customfeeds.conf`

```bash
src/gz openwrt_dist https://easypi.github.io/openwrt-dist/packages/base/{architecture}
src/gz openwrt_dist_luci https://easypi.github.io/openwrt-dist/packages/luci
```

Then

```bash
opkg update
opkg install ChinaDNS
opkg install luci-app-chinadns
opkg install dns-forwarder
opkg install luci-app-dns-forwarder
opkg install shadowsocks-libev
opkg install luci-app-shadowsocks
opkg install simple-obfs
opkg install ShadowVPN
opkg install luci-app-shadowvpn
```

You can also search and install them in LuCI.

### Use script

Use the following command and follow the prompts.

```bash
wget https://openwrt-dist.sourceforge.net/auto_install.sh
chmod +x auto_install.sh
./auto_install.sh
```

### Form Files

Use `SCP` or `FTP` upload these downloaded files to your router, then log in your router and use `opkg` to install these `.ipk` file.

Compile

The depot is composed of the following repository on GitHub.

- [ChinaDNS for OpenWrt](https://github.com/aa65535/openwrt-chinadns)
- [DNS-Forwarder for OpenWrt](https://github.com/aa65535/openwrt-dns-forwarder)
- [RedSocks2 for OpenWrt](https://github.com/aa65535/openwrt-redsocks2)
- [ShadowVPN for OpenWrt](https://github.com/aa65535/openwrt-shadowvpn)
- [LuCI Applications of OpenWrt-dist](https://github.com/aa65535/openwrt-dist-luci)
- [Shadowsocks-libev for OpenWrt](https://github.com/shadowsocks/openwrt-shadowsocks)
- [OpenWrt LuCI for Shadowsocks-libev](https://github.com/shadowsocks/luci-app-shadowsocks)

Use the [SDK](http://wiki.openwrt.org/doc/howto/obtain.firmware.sdk) to build (take openwrt-dist-luci for example): cd into SDK root, then

```bash
pushd package
git clone https://github.com/aa65535/openwrt-dist-luci.git
popd
make menuconfig # select LuCI / 3. Applications
make V=99
```

## License

GPLv3

## Bugs and Support

- [Google Groups](https://groups.google.com/d/forum/openwrt-dist)
