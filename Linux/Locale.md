---
title: Locale
description: 
parent: Linux
permalink: /docs/linux/locale
---

# Locale pr_BR.UTF-8

### Exibindo as configurações atuais

    locale

### Listando os Locales disponíveis no sistema

    locale -a

### Instalando um novo Locale

    locale-gen pt_BR.UTF-8

### Reconfigurando pacotes intalados

    dpkg-reconfigure locales

### Setando o locale padrão

    update-locale LANG=pt_BR.UTF-8

### Consulta o valor definido em LANG

    cat /etc/default/locale