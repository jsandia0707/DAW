ejemplo1 entramsoe en el directorio docker 
$ ls
Dockerfile  public_html
usamos imagen base
# syntax=docker/dockerfile:1
FROM debian:stable-slim
RUN apt-get update && apt-get install -y apache2 && apt-get clean && rm -rf /var/lib/apt/lists/*
WORKDIR /var/www/html/
COPY public_html .
EXPOSE 80
CMD apache2ctl -D FOREGROUND
creamos la imagen
$ docker build -t javiersand2/ejemplo1:v1 .
comprobamos que se alla creado
$ docker images
REPOSITORY             TAG                 IMAGE ID            CREATED             SIZE
javiersand2/ejemplo1     v1                  8c3275799063        1 minute ago      226MB

creamos un contenedor $ docker run -d -p 80:80 --name ejemplo1 josedom24/ejemplo1:v1
accedemos desde el navegador 
![image](https://github.com/user-attachments/assets/12643491-9ef1-4ecd-a50b-ff8bdbc46e70)

ejemplo 2 con php instalado 
# syntax=docker/dockerfile:1
FROM php:7.4-apache
COPY app /var/www/html/
EXPOSE 80
le damos forma y creamos el contenedor
$ docker build -t josedom24/ejemplo2:v2 .
$ docker run -d -p 80:80 --name ejemplo2 josedom24/ejemplo2:v2
accedemos a info.php
![image](https://github.com/user-attachments/assets/056b907b-d516-4a59-a7ee-a08d4d698e43)
ejemplo 3
usamos la imagen base
# syntax=docker/dockerfile:1
FROM debian:12
RUN apt-get update && apt-get install -y python3-pip  && apt-get clean && rm -rf /var/lib/apt/lists/*
WORKDIR /usr/share/app
COPY app .
RUN pip3 install --no-cache-dir --break-system-packages -r requirements.txt
EXPOSE 3000
CMD python3 app.py
creamos la imagen $ docker build -t josedom24/ejemplo3:v1 .
$ docker images
REPOSITORY             TAG                 IMAGE ID            CREATED             SIZE
javiersand2/ejemplo1     v1                  8c3275799063        1 minute ago      226MB
accedemos desde el navegador 
![image](https://github.com/user-attachments/assets/b975fd7b-1549-47ec-a76a-23744f12fa48)
