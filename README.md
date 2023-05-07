# «Keepalived/vrrp» | "Бойко Владислав"

---
## Задание 1
На интерфесе enp0s8 обоих машин настроенна внутренная сеть хоста 192.168.56.0/24, enp0s3 прокинут сетевой мост
### Мастер нода:
```java
vrrp_instance main {
state MASTER
interface enp0s8
virtual_router_id 10
priority 110
advert_int 4
authentication {
auth_type AH
auth_pass 1234
}
unicast_peer {
192.168.56.107
}
virtual_ipaddress {
192.168.56.100 dev enp0s8 label enp0s8:vip
}
}
```
![ip a](https://github.com/VladiSlave2042/Keepalived-vrrp/blob/main/img/ip%20a%20MASTER.png)
### Слейв нода:
```java
vrrp_instance main {
state BACKUP
interface enp0s8
virtual_router_id 10
priority 100
advert_int 4
authentication {
auth_type AH
auth_pass 1234
}
unicast_peer {
192.168.56.108
}
virtual_ipaddress {
192.168.56.100 dev enp0s8 label enp0s8:vip
}
}
```
![ip a](https://github.com/VladiSlave2042/Keepalived-vrrp/blob/main/img/ip%20a%20SLAVE.png)

---
## Задание 2