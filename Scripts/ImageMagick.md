---
title: ImageMagick
description: Convert, Edit, or Compose Bitmap Images
parent: Scripts
permalink: /docs/scripts/image-magick
---
# [ImageMagick](https://imagemagick.org/) - Convert, Edit, or Compose Bitmap Images 

Nos comandos abaixo `<input>` é o nome do arquivo de entrada e `<output>` é o nome do arquivo de saida que será criado.

### Redimencionando

    convert <input> -resize 2000x1000 <output>     # Target image will fit in 2000x1000 (but might be smaller, keeps aspects)
    convert <input> -resize 2000x     <output>     # Target image will be 2000px wide (keeps aspect ratio)
    convert <input> -resize x1000     <output>     # Target image will be 1000px high (keeps aspect ratio)
    convert <input> -resize 640x480!  <output>     # Target image will be exactly 640x480 (changes aspect ratio)

### Rotacionando

    convert <input> -rotate 90 <output>     # Rotates 90° clockwise
    
### Reduzindo qualidade

Para otimizar uma imagem PNG/JPG é só baixar a qualidade um pouco como no exemplo abaixo

    convert <input> -quality 80 <output>

 ou pode redimencionar com uma uma alta qualidade

    convert <input> -resize <size> -quality 95 <output>
    
