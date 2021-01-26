---
title: Postgres
description: 
parent: Databases
permalink: /docs/databases/postgres
related:
  databases: ['PgBouncer']
---

## Instalação

 ### Criar uma nova instancia/cluster
    pg_createcluster <version> <cluster name>

### Local da configuração padrão do postgres
    /etc/postgresql/<version>/main

### Local dados postgres
    /var/lib/postgresql/<version>/<cluster name>

### Local dos logs
    /var/log/postgresql/postgresql-<version>-<cluster name>.log

### Iniciando servico
    sudo service postgresql@<version>-<cluster name> start

### Parando servico
    sudo service postgresql@<version>-<cluster name> stop

### Iniciando servico
    sudo service postgresql@<version>-<cluster name> status

### Desabilitando o inicio automatico banco de dados main porta 5432 
    sudo nano /etc/postgresql/10/main/start.conf

## psql

### Conectando em uma base pelo psql

    sudo -u postgres psql -U user1 -p 16432 -h localhost db1

### Criar usuario no postgres e database

    postgres=# create user user1 password 'user1pass';
    postgres=# create database db1 owner user1;

Depois de criarr os usuários e necessário setar no pg_hba.conf para autenticar via md5

### Como listar os usuarios para add no arquivo userlist.txt

    psql -Atq -p 5434 -U postgres -d postgres -c "SELECT concat('\"', usename, '\" \"', passwd, '\"') FROM pg_shadow"

### Sair do psql
    \q

## SQL

### Using Regular Expressions

Você pode atualizar um campo usando expressões regulares com a função `regexp_replace()`

    UPDATE tabela SET campo = regexp_replace(campo, 'match pattern', 'replace string', 'g');

### Gerando JSON

Você pode gerar JSON no Postgres dessa forma:

    SELECT row_to_json(<name of key column>) FROM ...

### Analyze Queries

    EXPLAIN ANALYZE <sql statement>;


### Listar Clusters

    pg_lsclusters

### Listar configurações

    SHOW ALL;

### Mostrar diretorio de dados

     SHOW data_directory;

### Listar tamanho das bases

    SELECT pg_database.datname, pg_size_pretty(pg_database_size(pg_database.datname)) AS size FROM pg_database;

### Listar Querys em execução

    SELECT * FROM pg_stat_activity;

### Listar os Locks

    SELECT bl.pid AS blocked_pid, a.usename AS blocked_user, 
         kl.pid AS blocking_pid, ka.usename AS blocking_user
    FROM pg_catalog.pg_locks bl
       JOIN pg_catalog.pg_stat_activity a
       ON bl.pid = a.pid
       JOIN pg_catalog.pg_locks kl
            JOIN pg_catalog.pg_stat_activity ka
            ON kl.pid = ka.pid
       ON bl.transactionid = kl.transactionid AND bl.pid != kl.pid
    WHERE NOT bl.granted ;

### Consultando a uso de Tabelas

Se você quiser saber os acessos ou E / S por tabela ou índice, você pode usar as relações pg_stat _ * _ tables e pg_statio _ * _ tables. Por exemplo:

    SELECT * FROM pg_statio_user_tables;

para mostrar o I / O causado por suas relações. Ou para o número de acessos e tipos de varredura e tuplas buscados:

    SELECT * FROM pg_stat_user_tables;

## Solução de problemas

### Mudando configurações sem reiniciar

    ALTER SYSTEM SET <setting> TO <value>;
    SELECT pg_reload_conf();

### Matando conexões

Obtendo o PID:

    SELECT procpid, current_query FROM pg_stat_activity;

e matando atravez do PID

    SELECT pg_terminate_backend('12345');

### Uma forma mais genérica para matar todas as conexões de uma vez:
Substitua "TARGET_DB" pelo nome do banco de dados cujas conexões devem ser eliminadas.

    SELECT pg_terminate_backend(pg_stat_activity.procpid) FROM pg_stat_activity WHERE pg_stat_activity.datname = 'TARGET_DB';


## Pooling / Failover / Load Balance / HA

- [PgPool II](http://pgpool.net)

- [repmgr](http://www.repmgr.org/) que gerencia e monitora a replicação e tem promoção automática de escravo em caso de falha do mestre.

- [Escalando Postgres com pgpool e pgbouncer](https://girders.org/2012/09/scaling-postgresql-with-pgpool-and-pgbouncer.html)

