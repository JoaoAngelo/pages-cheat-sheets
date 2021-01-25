---
title: OpenSSL
description: Open Source Secure Sockets Layer
parent: Seguranca
permalink: /docs/seguranca/openssl
related:
  seguranca: ['SSL-Certificates']
---
# OpenSSL - Open Source Secure Sockets Layer

## Comandos OpenSSL

-   [OpenSSL Codebase](https://www.freecodecamp.org/news/openssl-command-cheatsheet-b441be1e8c4a/):
    Os comandos mais comuns para criar chaves e certificados.

-   Extraindo informações de certificados x509:

        openssl x509 -text -in my.pem
        openssl ca -text -in my_ca.pem
        openssl req -text -in csr.pem

-   Validando Arquivos

        openssl req -text -noout -verify -in csr.pem
        openssl rsa -in my.key -check
        openssl pkcs12 -info -in keystore.p12

-   Removendo senha de chaves

        openssl rsa -in key-with-pwd.pem -out key-without-pwd.pem


