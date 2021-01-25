---
title: SSL-Certificates
description: Secure Sockets Layer Certificates
parent: Seguranca
permalink: /docs/seguranca/ssl-certificates
related:
  seguranca: ['HTTPS', 'OpenSSL']
---
# SSL-Certificates - Secure Sockets Layer Certificates

## Utilizando Certbot

Exemplo gerando certificados com o letsencrypt e certbot

    certbot certonly --manuel --preferred-challenges dns -d example.com,www.example.com,upload.example.com,img.example.com

## Certificadoras Gratuitas

-   Cloudflare
-   StartSSL
-   [letsencrypt.org](https://letsencrypt.org/)

