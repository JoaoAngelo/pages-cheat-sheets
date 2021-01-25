---
title: SSL-Certificates
description: Secure Sockets Layer Certificates
parent: Seguranca
permalink: /docs/seguranca/ssl-certificates
related:
  seguranca: ['HTTPS', 'OpenSSL']
---
# SSL-Certificates - Secure Sockets Layer Certificates

## Certificados Gratuitos

-   Cloudflare
-   StartSSL
-   [letsencrypt.org](https://letsencrypt.org/)

## Certificado gratuito com certbot, Letsencrypt e DNS challenger da DigitalOcean

    certbot certonly --dns-digitalocean --dns-digitalocean-credentials key-digitalocean.ini --dns-digitalocean-propagation-seconds 60 -d example.com -d www.example.com -d upload.example.com -d img.example.com

### caminho que o certificado é gerado

    /etc/letsencrypt/live/example.com/fullchain.pem

### gerando certificado para o [tomcat](/docs/devops-services/tomcat) pelo certificado Letsencrypt

    openssl pkcs12 -export -out pkcs12.p12 -in fullchain.pem -inkey privkey.pem -name tomcat

    keytool -importkeystore -srckeystore pkcs12.p12 -srcstoretype PKCS12 -srcstorepass maisUmaSenha -deststorepass minhaSenha -destkeypass minhaOutraSenha -destkeystore keystore.jks -alias tomcat

### gerando certificado para o [tomcat](/docs/devops-services/tomcat) pelo certificado da Locaweb

    openssl pkcs12 -export -out star_example_com_br_pkcs12.pfx -in star_example_com_br_primary.crt -inkey star_example_com_br_key.key 

    keytool -importkeystore -srckeystore star_example_com_br_pkcs12.pfx -srcstoretype pkcs12 -destkeystore star_example_com_br_keystore.jks -deststoretype JKS
