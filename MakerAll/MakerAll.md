---
title: MakerAll
permalink: /docs/maker-all
nav_order: 2
---
# Dicas Softwell Maker

## Redirecionamento automático via .jsp

    <%
    response.setStatus(301);
    response.setHeader( "Location", "open.do?sys=SIGLA_SISTEMA" );
    response.setHeader( "Connection", "close" );
    %>