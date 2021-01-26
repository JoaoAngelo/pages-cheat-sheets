---
title: Tomcat
description: 
parent: DevOps Services
permalink: /docs/devops-services/tomcat
---

# Tomcat

### Reiniciar Tomcat
    sudo service tomcat restart

## Configuração de memoria

    sudo nano /etc/default/tomcat

## Ver log do catalina
    sudo tail -f /var/log/tomcat/catalina.out

### We put the tomcat user as the owner of the folder of tomcat:

    chown -R tomcat:tomcat /opt/tomcat

### Users can not modify the configuration of tomcat:

    chmod -R g+r /opt/tomcat/conf

### Users can modify the other folders:

    chmod -R g+w /opt/tomcat/logs
    chmod -R g+w /opt/tomcat/temp
    chmod -R g+w /opt/tomcat/webapps
    chmod -R g+w /opt/tomcat/work

### Activate the sticky-bit for new files keep permissions defined:

    chmod -R g+s /opt/tomcat/conf
    chmod -R g+s /opt/tomcat/logs
    chmod -R g+s /opt/tomcat/temp
    chmod -R g+s /opt/tomcat/webapps
    chmod -R g+s /opt/tomcat/work

### Finally, we add the tomcat group we want users who can use the tomcat:

    usermod -a -G tomcat MYUSER
    usermod -a -G tomcat www-data