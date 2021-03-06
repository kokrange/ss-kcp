# ss-kcp
An easy-to-deploy project for ss-kcp.

## Prerequisite
0. Buy your oversea Linux cloud server, and get *your_server_ip*.
1. Install docker on server:
```shell
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER
```
2. Install docker compose on server:
```shell
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## Server deployment
1. Change **your_ss_password**, **your_kcp_key** and **your_server_port** in **docker-compose.yaml** to your customized values.
2. Copy **docker-compose.yaml** to your server and run
```shell
docker-compose up -d
```
3. Done!

## Client configuration
* MacOS [ssNG](https://github.com/shadowsocks/ShadowsocksX-NG/releases/tag/v1.9.4) Server Preference
  * Address: **your_server_ip** : **your_server_port**
  * Encryption: chacha20-ietf-poly1305
  * Password: **your_ss_password**
  * Plugin: kcptun
  * Plugin Opts: key=**your_kcp_key**;crypt=salsa20;mode=fast3;mtu=1350;sndwnd=1024;rcvwnd=1024;datashard=10;parityshard=3;conn=30;autoexpire=3600;dscp=0

* Windows 10 [ss-windows](https://github.com/shadowsocks/shadowsocks-windows/releases/tag/4.1.9.2), [kcptun-windows](https://github.com/shadowsocks/kcptun/releases/tag/v20170718)
  * Extract *Shadowsocks-4.1.9.2.zip*, copy **Shadowsocks.exe**.
  * Extract *kcptun-windows-amd64-20170718.tar.gz*, rename **client_windows_amd64.exe** to **kcptun.exe**, copy **kcptun.exe**.
  * **[IMPORTANT]** Put **Shadowsocks.exe** and **kcptun.exe** in the *SAME* directory. Then run **Shadowsocks.exe**
  * Server Preference is the same as in MacOS.

* Android [ss-android](https://github.com/shadowsocks/shadowsocks-android/releases/download/v5.2.3/shadowsocks--universal-5.2.3.apk), [kcptun-android](https://github.com/shadowsocks/kcptun-android/releases/download/v1.0.1/kcptun--universal-1.0.1.apk)
  * Install ss, kcptun on your android device.
  * Server Preference is the same as in MacOS.
