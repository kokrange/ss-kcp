# ss-kcp
A easy-to-deploy project for ss-kcp.

## Prerequisite
1. Install docker:
```shell
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER
```
2. Install docker compose:
```shell
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## Server deployment
1. Change your_ss_password, your_kcp_key, and your_server_port in docker-compose.yaml to your customized values.
2. Copy docker-compose.yaml to your server and run
```shell
docker-compose up -d
```
3. Done!

## Client configuration
* MacOS [ssNG](https://github.com/shadowsocks/ShadowsocksX-NG/releases/tag/v1.9.4) Server Preference
  * Address: your_server_ip : your_server_port
  * Encryption: chacha20
  * Password: your_ss_password
  * Plugin: kcptun
  * Plugin Opts: key=your_kcp_key;crypt=aes;mode=fast3;mtu=1350;sndwnd=1024;rcvwnd=1024;datashard=10;parityshard=3;dscp=0
  * Remarks: ss-kcp
