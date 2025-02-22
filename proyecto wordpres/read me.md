Creamos una VPC con dos subredes públicas y dos privadas.
vamos a aws y buscamos vpc
![image](https://github.com/user-attachments/assets/73c6bd4c-31f6-449d-bb5d-c1fb86fdc59e)
accedemos a vpc
![image](https://github.com/user-attachments/assets/380b1432-ab24-4f11-b5f0-d9063f220a65)
creamos la vpc
![image](https://github.com/user-attachments/assets/c71b362e-d2fa-4d90-900c-e1b778a391d0)
Configure los siguientes parámetros:

Nombre del VPC: wordpress-vpc.

Bloque CIDR IPv4: 10.0.0.0/16(puedes usar otro rango si lo prefieres).

Bloque CIDR IPv6: Opcional (puedes dejarlo deshabilitado si no necesitas IPv6).

Tenencia: Default.
![image](https://github.com/user-attachments/assets/00ba5937-6192-4e40-a669-f7a2c90af13f)
creamos las rubredes publicas 
vamos a subredes 
![image](https://github.com/user-attachments/assets/ce66f428-6e7d-4b00-9728-ce74709f5ecb)
![image](https://github.com/user-attachments/assets/50331eb3-5bca-4c01-994f-ac4a31cb2f88)

Configure los siguientes parámetros para la primera subred pública:

Nombre de la subred: subred-publica-1.

VPC:Selecciona wordpress-vpc.

Zona de disponibilidad (AZ): Selecciona una AZ, por ejemplo, us-east-1a.

Bloque CIDR IPv4: 10.0.1.0/24.
![image](https://github.com/user-attachments/assets/de934eeb-e6b1-4179-a344-3cf64640f569)

![image](https://github.com/user-attachments/assets/c22a33c3-2a6c-4981-93c6-cd23452cdb56)
creamos las dos subredes pribadas a traves del mismo proceso
creamos una puerta de enlade 
![image](https://github.com/user-attachments/assets/8059cbd6-a579-45dd-9d14-f7c876294eb2)
![image](https://github.com/user-attachments/assets/c248d65c-bc16-4912-8c37-073f552688e9)
![image](https://github.com/user-attachments/assets/e8d07740-c5ed-4615-a5e7-40fea0bfb137)
Una vez creada, selecciona la puerta de enlace y haz clic en el botón Acciones > Adjuntar a VPC , luego selecciona tu VPC ( wordpress-vpc).
![image](https://github.com/user-attachments/assets/a982c828-05c1-48a3-ac67-c4e932bfc0f4)
![image](https://github.com/user-attachments/assets/4f3543b2-1a6c-446e-86e3-d252d591b84e)
configuramos las tablas de ruta 
![image](https://github.com/user-attachments/assets/f83697fa-3ef4-4662-94c3-3907f0dd3d07)
Renómbrala como tabla-rutas-publicas para mantenerla organizada.
![image](https://github.com/user-attachments/assets/bc99cd47-f118-472c-ae77-b648319da64a)
Edita las rutas y añade lo siguiente:

Destino:0.0.0.0/0

Target (Destino): Selecciona tu Gateway de Internet ( wordpress-gateway).
![image](https://github.com/user-attachments/assets/9e26d83e-d19a-4122-89d5-4878c8e4e920)
asociamos la tabla a las sub redes publicas
![image](https://github.com/user-attachments/assets/3f8bd049-925f-492d-a660-142f75e6979e)
![image](https://github.com/user-attachments/assets/c8268421-c8de-458c-a6ed-1234e7d77459)

ahora repetimos el proceso para la tabla y subredes privadas
![image](https://github.com/user-attachments/assets/efe7267f-f3b5-48ea-8406-368d49e4cab1)
No añadas ninguna ruta adicional (las subredes privadas no necesitan acceso directo a Internet).
![image](https://github.com/user-attachments/assets/bcf065e4-dfdf-4386-9083-21236db1b056)

creamos la instancia conectando la vpc
![image](https://github.com/user-attachments/assets/cfc7df24-8b15-450a-a5c7-9829bcff30b1)

![image](https://github.com/user-attachments/assets/397d031e-51c0-4304-a904-ff85e3a4e5e6)
actualizamos los paquetes del sistema :
sudo apt update
sudo apt upgrade -y

![image](https://github.com/user-attachments/assets/892e6551-0b96-4d88-862b-d83ec1ba492b)
![image](https://github.com/user-attachments/assets/7a5edae8-6b24-4c2b-bdd3-dad82d2fbdfc)
instalamos el servidor apache con: sudo apt install apache2 -y
![image](https://github.com/user-attachments/assets/1d441d54-d873-431a-8ab6-cb8a8a2a2254)
iniciamos el servidor apache:sudo systemctl start apache2
![image](https://github.com/user-attachments/assets/6e725ec5-c852-4edd-9c2b-5ddcef3a7a56)
(opcional)configuramos Apache para que se inicie automáticamente al arrancar la instancia de aws ec2 :sudo systemctl enable apache2
![image](https://github.com/user-attachments/assets/2c3c1513-f357-45c0-ab57-f8770c18c1c9)
procedemos a instalar php: sudo apt install php libapache2-mod-php php-mysql -y
![image](https://github.com/user-attachments/assets/1aec7814-9257-443a-ad4b-44cfddb7f080)

![image](https://github.com/user-attachments/assets/2bd3f824-7fc9-4010-ab6e-51146378548f)
reiniciamos apache 
![image](https://github.com/user-attachments/assets/64f55cf3-b01f-48d9-a500-b1c54f3a7fae)
verificamos la instalacion creando un archivo .php:echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php

![image](https://github.com/user-attachments/assets/29b3d6ae-546d-4d95-a522-1c5aa96abd46)
comprovamos con la siguiente ruta:http://ec2-52-23-171-213.compute-1.amazonaws.com/info.php
![image](https://github.com/user-attachments/assets/bc4f938d-2608-4bc7-b6ec-6a6831597a11)

eliminamos el archivo para mas seguridad:sudo rm /var/www/html/info.php
![image](https://github.com/user-attachments/assets/821fad36-606a-4e60-b0c7-20772471fd93)
![image](https://github.com/user-attachments/assets/0f25a59d-adbd-4c82-9b64-1f6d4462dfac)
buscamos el servicio rds

![image](https://github.com/user-attachments/assets/e6f213d9-c254-4358-8d66-7a8fdb5bb739)
accedemos al apartado base de datos 
![image](https://github.com/user-attachments/assets/e714cd21-b92d-49e8-a3d9-d4fbdb5c781c)

creamos la base de datos rds 
Elige "Creación estándar" para tener más opciones de configuración.

En "Opciones del motor", selecciona MySQL como motor de base de datos.
![image](https://github.com/user-attachments/assets/4e9c4157-30b4-40fa-b7aa-e58acce1f936)
En "Plantillas", elige "Capa gratuita" para evitar cargos.
Configure los siguientes parámetros:

Nombre de la base de datos: Elige un nombre descriptivo

Nombre de usuario maestro: Definir un nombre de usuario

Contraseña maestra: Establece una contraseña segura
![image](https://github.com/user-attachments/assets/a0ba500b-b9bd-4c5c-9c19-0775e5d2b809)
En "Conectividad", nos aseguramos de que la base de datos esté en la misma VPC que su instancia EC2.
![image](https://github.com/user-attachments/assets/8f369b0e-ad5a-40f4-902a-47418811d61e)
Configure el grupo de seguridad para permitir el tráfico entrante desde su instancia EC2.
![image](https://github.com/user-attachments/assets/f3d0d809-b8bf-45c9-8a0f-9b6f0365c1b0)
Mantén las demás opciones por defecto y haz clic en "Crear base de datos".
![image](https://github.com/user-attachments/assets/c1297cd2-1c2b-402a-bc67-07df2142e771)
buscamos el servicio EFS 
![image](https://github.com/user-attachments/assets/1ab99c16-67b7-4bb2-ab1a-65403858e0d9)

Cree un sistema de almacenamiento EFS.
![image](https://github.com/user-attachments/assets/30f4c85a-99bf-4555-8e74-7c6283c420ce)
instalamos el paquete nfs-common : sudo apt install nfs-common
![image](https://github.com/user-attachments/assets/acd88cef-b7df-4d7a-ab5c-74e5fa2f5068)

![image](https://github.com/user-attachments/assets/cff17875-f28b-4e75-8f60-e9650ed85cd8)

Montar el EFS en la instancia: sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-0c78c0d35e7e930af.efs.us-east-1.amazonaws.com:/ /mnt/efs
![image](https://github.com/user-attachments/assets/05dca313-4687-4de1-b0da-1a203e88a4f0)

descargamos he instalamos wordpress
cd /var/www/html
sudo wget http://wordpress.org/latest.tar.gz
sudo tar -xzf latest.tar.gz
![image](https://github.com/user-attachments/assets/c1141c1a-3637-4903-b9a3-99000597bc5a)
configuramos la base de datos para worpress: sudo nano wp-config.php
define( 'DB_NAME', 'nombre_de_la_base_de_datos' );
define( 'DB_USER', 'nombre_de_usuario' );
define( 'DB_PASSWORD', 'contraseña_del_usuario' );
define( 'DB_HOST', 'localhost' );
Reemplaza los valores entre comillas con la información correcta de tu base de datos RDS:

DB_NAME: El nombre de tu base de datos en RDS

DB_USER: El nombre de usuario de la base de datos

DB_PASSWORD: La contraseña de la base de datos

DB_HOST: El punto de enlace de tu instancia RDS
Nos conectamos a la instancia de la base de datos.
![image](https://github.com/user-attachments/assets/d1b34496-d192-42c1-b832-f23a928bb7e4)
Creamos Base de datos, usuario y contraseña:
CREATE DATABASE wordpress; 
CREATE USER 'wordpress_user'@'%' IDENTIFIED BY 'password123'; 
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress_user'@'%'; 
FLUSH PRIVILEGES;
![image](https://github.com/user-attachments/assets/db39df0e-41db-4f2e-9403-79c3ea0fa931)

Lanzamos la instalación simplemente llamando al servidor web en el navegador:http://44.192.41.132/wordpress
![image](https://github.com/user-attachments/assets/9e626e0c-81fd-4ebb-8adc-3e3fc23358e7)
Proporcionamos los datos que nos pide acerca de la base de datos y seguimos el asistente hasta completar la instalación de wordpress.
![image](https://github.com/user-attachments/assets/c669b5c6-5c2f-4628-86ea-2d1adc50d105)
creamos el archivo wp-config.php y pegamos lo que wordpres nos proporciona
![image](https://github.com/user-attachments/assets/b78dc2da-ee86-4370-943b-b65ad824072a)
![image](https://github.com/user-attachments/assets/ab7f5e48-55dd-4f2f-b863-c60a6555254b)
terminamos la instalacion
![image](https://github.com/user-attachments/assets/6c37fe68-bacb-49f7-b193-22303c57726e)
y tras iniciar sesion 
![image](https://github.com/user-attachments/assets/81d26030-0fb6-4c91-8cec-2ac6f523a11f)










