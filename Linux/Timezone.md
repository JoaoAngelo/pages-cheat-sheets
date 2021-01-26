---
title: Timezone
description: 
parent: Linux
permalink: /docs/linux/timezone
---

# timezone

### Exibir o timezone atual

    timedatectl
    ou
    ls -l /etc/localtime
    ou
    cat /etc/timezone   

### Listar os timezones disponíveis

    timedatectl list-timezones

### Definir um timezone

    timedatectl set-timezone America/Sao_Paulo
