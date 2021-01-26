---
title: Network
description: 
parent: Linux
permalink: /docs/linux/network
---

## Listar IP

    ip a
    ou
    ip route
    ou
    ifconfig

## Configurar interface de Rede Virtual

Abrir o arquivo:

    nano /etc/network/interfaces

Adicionar a configuração com base nesse exemplo:

    auto vmbr2
    iface vmbr2 inet static
    address 192.168.0.254
    netmask 255.255.255.0
    bridge_ports none
    bridge_stp off
    bridge_fd 0
    post-up echo 1 > /proc/sys/net/ipv4/ip_forward
    post-up iptables -t nat -A POSTROUTING -s '192.168.0.0/24' -o vmbr0 -j MASQUERADE
    post-down iptables -t nat -D POSTROUTING -s '192.168.0.0/24' -o vmbr0 -j MASQUERADE

    # VM-WEB HTTP 80:192.168.0.1:80
    post-up iptables -t nat -A PREROUTING -i vmbr0 -p tcp --dport 80 -j DNAT --to 192.168.0.1:80
    post-down iptables -t nat -D PREROUTING -i vmbr0 -p tcp --dport 80 -j DNAT --to 192.168.0.1:80

