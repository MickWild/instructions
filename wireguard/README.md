#### 1. Update database of available packages for apt

```shell
 sudo apt update
```
#### 2. Install wireguard

```shell
 sudo apt install -y wireguard
```

#### 3. 

```shell
 wg genkey | tee /etc/wireguard/privatekey | wg pubkey | tee /etc/wireguard/publickey
```

#### 4. 

```shell
sudo nano wg0.conf
```
```shell
[Interface]
PrivateKey = <privatekey>
Address = 10.0.0.1/24 
ListenPort = 55555 
PostUp = iptables -A FORWARD -i %i -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE 
```

#### 5. 

```shell
$ echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf
```

#### 6. 

```shell
systemctl enable wg-quick@wg0.service
```

#### [Clients](https://shadowsocks.org/en/download/clients.html) for connection