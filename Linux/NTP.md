---
title: NTP
description: Network Time Protocol
parent: Linux
permalink: /docs/linux/ntp
---

# NTP - Network Time Protocol

### Instalando NTP

    sudo apt-get update && apt-get install ntp ntpdate

### Sincronizando o relógio doo sistema (necessário fazer apenas quando acontecer alguma desincronização)

    service ntp stop
    ntpdate a.ntp.br
    service ntp start

### Setando configurações do servidor no NTP

    sudo nano /etc/ntp.conf

#### configurações padrões:

    server 0.ubuntu.pool.ntp.org
    server 1.ubuntu.pool.ntp.org
    server 2.ubuntu.pool.ntp.org
    server 3.ubuntu.pool.ntp.org
    # Use Ubuntu's ntp server as a fallback.
    server ntp.ubuntu.com

#### configurações do servidor brasileiro:

    server a.ntp.br
    server b.ntp.br
    server c.ntp.br
    # Use Ubuntu's ntp server as a fallback.
    server ntp.ubuntu.com

### Iniciando, Parando e Reiniciando o serviço NTP

    service ntp start
    service ntp stop
    service ntp restart