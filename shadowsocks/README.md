1. Update database of available packages for apt

```bash
$ sudo apt update
```
2. Install shadowsocks

```bash
$ apt install shadowsocks-libev
```

3. Then edit the shadowsocks config file

```bash
$ nano /etc/shadowsocks-libev/config.json
```
```bash
{
    "server":["your ip address"],
    "mode":"tcp_and_udp",
    "server_port":your ip port,
    "local_port":1080,
    "password":"your ip password",
    "timeout":60,
    "method":"chacha20-ietf-poly1305"
}
```

4. Restart shadowsocks service

```bash
$ sudo systemctl restart shadowsocks-libev
```