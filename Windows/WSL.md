---
title: WSL
description: Windows Subsystem for Linux
parent: Windows
---

## Instalação 

Instalar o WSL pelo CLI

    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

Habilitar o suporte ao WSLv2

    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

Forçar rodar as distros com WSLv2 como padrão

    wsl --set-default-version 2

## Gerenciar Distribuições Instaladas

    wsl -l [-v]                    # Lista as distros instaladas
    wsl --set-default <name>       # Seta a distro padrão
    wsl --set-version <name> 1     # Força uma distro a rodar no WSLv1
