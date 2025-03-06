hare los ejemplos 1,2y3
ejemplo1

docker network create red_guestbook
![image](https://github.com/user-attachments/assets/8eeec12d-12e8-46bf-a7fd-3d4fff81e63c)
ejecutamos los contenedores docker run -d --name redis --network red_guestbook -v /opt/redis:/data redis redis-server --appendonly yes
![image](https://github.com/user-attachments/assets/6a28973e-b8a3-4641-9f18-620bffd9ddfa)
docker run -d -p 80:5000 --name guestbook --network red_guestbook iesgn/guestbook
![image](https://github.com/user-attachments/assets/8b5755b0-9bee-45de-913e-6c9c6ea78ab5)
vemos la aplicacion 

![image](https://github.com/user-attachments/assets/e0688065-8df9-4607-b818-85f9912e8ba7)

ejemplo 3
docker network create red_wp
instalacion de wordpres

![image](https://github.com/user-attachments/assets/2b1d95d5-2ac3-4524-8342-eaa98ef1f075)

creamos los contenedores
docker run -d --name servidor_mysql \
                --network red_wp \
                -v /opt/mysql_wp:/var/lib/mysql \
                -e MYSQL_DATABASE=bd_wp \
                -e MYSQL_USER=user_wp \
                -e MYSQL_PASSWORD=asdasd \
                -e MYSQL_ROOT_PASSWORD=asdasd \
                mariadb


                ![image](https://github.com/user-attachments/assets/81455a17-ddcc-4b16-a379-182b74f27ec4)
docker run -d --name servidor_wp \
                --network red_wp \
                -v /opt/wordpress:/var/www/html/wp-content \
                -e WORDPRESS_DB_HOST=servidor_mysql \
                -e WORDPRESS_DB_USER=user_wp \
                -e WORDPRESS_DB_PASSWORD=asdasd \
                -e WORDPRESS_DB_NAME=bd_wp \
                -p 80:80 \
                wordpress

                ![image](https://github.com/user-attachments/assets/2e14bc6a-67bb-4a11-9322-ddc4bb11b335)
muestro los contenedores
![image](https://github.com/user-attachments/assets/9038d7ae-e21d-4db7-9d6b-4a1fb02455a7)
habrimos en wordpres
![image](https://github.com/user-attachments/assets/5dd1041d-cb5e-4f6c-9d80-c9c8dbaaf1ab)
ejemplo 2
creamos la red de contenedores
docker network create red_temperaturas
![image](https://github.com/user-attachments/assets/3f5bd323-2fa5-4cf4-b42b-d217eb7fe822)

docker run -d --name temperaturas-backend --network red_temperaturas iesgn/temperaturas_backend
![image](https://github.com/user-attachments/assets/d2fc4706-0e58-4434-b186-8090b342ed90)
docker run -d -p 80:3000 --name temperaturas-frontend --network red_temperaturas iesgn/temperaturas_frontend
![image](https://github.com/user-attachments/assets/eaac53b1-6304-4eda-9a4f-48cc157007e9)

