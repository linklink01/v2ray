# v2fly-core

This use `docker-compose` to start v2ray.

## Install docker

```
sudo yum -y install docker
```

## Install docker-compose

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
sudo chmod +x /usr/bin/docker-compose
```

## Write v2ray configuration

```
sudo mkdir -pv /etc/v2ray/
sudo vim /etc/v2ray/config.json
```

> 1. Examples available at [v2fly/v2ray-examples](https://github.com/v2fly/v2ray-examples).
> 2. Configuration file `config.json` can also be generated by [2dust/v2rayN](https://github.com/2dust/v2rayN).

## Run container

```
git clone https://github.com/LinuxHub-Group/docker-compose-v2fly-core.git
cd ./docker-compose-v2fly-core/
sudo docker-compose -f ./docker-compose.yml up -d
```

## Check v2ray

```
$ sudo docker logs v2fly-core
Emulate Docker CLI using podman. Create /etc/containers/nodocker to quiet msg.
V2Ray 4.41.1 (V2Fly, a community-driven edition of V2Ray.) Custom (go1.16.6 linux/amd64)
A unified platform for anti-censorship.
2021/09/18 08:10:38 [Info] main/jsonem: Reading config: /etc/v2ray/config.json

$ sudo netstat -ntulp | grep v2ray
tcp6       0      0 :::10808                :::*                    LISTEN      577594/v2ray
tcp6       0      0 :::10809                :::*                    LISTEN      577594/v2ray
udp6       0      0 :::10808                :::*                                577594/v2ray
```

