---
title: PgBouncer
description: 
parent: Databases
permalink: /docs/databases/pgbouncer
related:
  databases: ['Postgres']
---
# PgBouncer

## Instalação

    sudo apt-get update && apt-get install pgbouncer

## Listar comandos

    pgbouncer --help

## Arquivo de configurações

    sudo nano /etc/pgbouncer/pgbouncer.ini 

### Debugando PgBouncer

Para inspecionar as operações do PgBouncer é necessário ter um usuário definido no arrquivo de credenciais (ex.: /etc/pgbouncer/userlist.txt) e definido a chave "stats_users" no arquivo pgbouncer.ini:

    stats_users = myuser

Use este usuário para se conectar na base "pgbouncer" pelo psql:

    psql -p 6432 -U myuser -W pgbouncer

Listando os comandos do psql:

    SHOW HELP;

O PgBouncer irá apresentar uma lista dos comandos aceitaveis:

    pgbouncer=# SHOW HELP;
    NOTICE:  Console usage
    DETAIL:  
        SHOW HELP|CONFIG|DATABASES|POOLS|CLIENTS|SERVERS|VERSION
        SHOW STATS|FDS|SOCKETS|ACTIVE_SOCKETS|LISTS|MEM
        SET key = arg
        RELOAD
        PAUSE []
        SUSPEND
        RESUME []
        SHUTDOWN

Os comandos "SHOW" são auto explicativos. uito úteis são os comandos "SUSPEND" e "RESUME" quando você usa pools.

### Online Restart

Se você precisar reiniciar o pgbouncer sob carga de tráfego, use "-R" para evitar a desconexão dos clientes. Esta opção faz com que o novo processo reutilize os soquetes Unix do antigo. Um possível caso de uso pode ser que você pense que o pgbouncer ficou travado, sobrecarregado ou instável.

    pgbouncer -R

Além disso, na maioria dos casos, SIGHUP deve resolver.

### Pooler Error: Auth Failed

Se as conexões com a configuração do pgbouncer falharem com "Erro de Pooler: Falha na autenticação", verifique os seguintes valores de configuração no pgbouncer.ini

-   **auth_file = ...** : Certifique-se de apontar este caminho para o arquivo pg_auth na configuração do Postgres.
-   **auth_type = ...** : Certifique-se de definir o tipo de autenticação correto. Por exemplo. "md5" para senhas com hash MD5.
-   Verifique se o seu arquivo pg_auth possui as entradas de senhas necessárias.

