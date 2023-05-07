# «Keepalived/vrrp» | "Бойко Владислав"

---
## Задание 1
На интерфесе enp0s8 обоих машин настроенна внутренная сеть 192.168.10.0/24 без ipV6 на интерфейсах enp0s3 прокинут сетевой мост, enp0s9 пока опустим, это на будущее
### Мастер нода:
vrrp_instance failover_test {
state MASTER
interface enp0s8
virtual_router_id 10
priority 110
advert_int 4
authentication {
auth_type AH
auth_pass 1111
}
unicast_peer {
192.168.10.1
}
virtual_ipaddress {
192.168.10.50 dev enp0s8 label enp0s8:vip
}
}
![ip a](https://github.com/VladiSlave2042/Keepalived-vrrp/blob/main/img/ip%20a%20MASTER.png)
### Слейв нода:
vrrp_instance failover_test {
    state BACKUP
    interface enp0s8
    virtual_router_id 10
    priority 110
    advert_int 4
    authentication {
        auth_type AH
        auth_pass 1111
        }
        unicast_peer {
            192.168.10.2
            }
            virtual_ipaddress {
                192.168.10.50 dev enp0s8 label enp0s8:vip
                }
                }

![ip a](https://github.com/VladiSlave2042/Keepalived-vrrp/blob/main/img/ip%20a%20SLAVE.png)

---
## Задание 2