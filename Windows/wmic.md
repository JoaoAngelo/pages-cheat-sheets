---
title: WMIC
description: Windows Management Instrumentation Command-line
---

## Exemplos

Obtendo informações do sistema

    wmic bios get Manufacturer,Name,Version
    wmic diskdrive get model,name,freespace,size         # discos fisicos 
    wmic logicaldisk get name                            # discos lógicos
    
    wmic printer list status
    wmci printerconfig list
    wmic os list brief                         # Informações do Windows
    wmic product list brief                    # programas instalados  
    
    wmic startup list full

Para executar em modo interativo

    wmic

use "quit" ou "exit" para sair do modo interativo.

## Gerenciar Processos

Listar os processos rodando

    wmic process list
    wmic process list brief
    wmic process list brief find "calc.exe"
    wmic process list full

Iniciando e matando um processo

    wmic process call create "calc.exe"
    wmic process where name="calc.exe" call terminate

Setando prioridade de um processo

    wmic process where name="calc.exe" call setpriority 64

Listando variáveis de ambiente

    wmic environment list

## Gerenciamento de Usuários

    wmic group list brief
    wmic useraccount list
    wmic sysaccount list
    
## Atualizações

    wmic qfe list           # Listar atualizações pendentes

## Remote Access

Executando comandos em outra máquina (remoto), Ex.:

    wmic /node:<ip> /user:<user> /password:<password> os list brief

Habilitando o RDP remotamente, bem bacana esse!

    wmic /node:<ip> /user:<user> /password:<password> RDToggle where ServerName=<server name> call SetAllowTSConnections 1
