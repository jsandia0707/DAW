Práctica Servidores web
1º trimestre
Paso 1: Instalación del Servidor Apache
    1.  Instalar Apache
       
sudo apt update
![image](https://github.com/user-attachments/assets/9b795743-0553-41d1-a4dd-e804e0d94f39)

sudo apt install apache2
![image](https://github.com/user-attachments/assets/bb8da48f-50da-4e2e-a454-1507f71d85d1)

Paso 2: configurar el archivo /etc/hosts
Edite el archivo /etc/hostspara agregar los dominios locales.
![image](https://github.com/user-attachments/assets/9bb125ef-26eb-452c-bd59-1548de93acdc)

sudo nano /etc/hosts
Guarda y cierra el archivo.
Paso 3: Configurar Virtual Hosts para cada dominio
    1. VirtualHost para centro.intranet (WordPress):
       Crea el archivo /etc/apache2/sites-available/centro.intranet.conf:
       ![image](https://github.com/user-attachments/assets/0fbbe6a9-6eba-45d9-afde-61ba498a0773)

       Luego, habilita el sitio: 
       ![image](https://github.com/user-attachments/assets/c394dcc9-df67-45bf-9ad4-7f0fd91f93a1)


4. Habilitar módulos de Apache
sudo a2enmod rewrite
sudo a2enmod swgi falla por que no tenemos el modulo wsgi
![image](https://github.com/user-attachments/assets/e83cd9b1-27c0-48b0-b2e8-76fdcf4cf3cd)

instalamos el modulo mod_wsgi
![image](https://github.com/user-attachments/assets/ba05117b-020d-4539-a8ea-9129542bcb40)

6. Instalar WordPress
Descarga WordPress 
wget https://wordpress.org/latest.tar.gz
tar -xzvf latest.tar.gz -C /var/www/centro --strip-components=1
![image](https://github.com/user-attachments/assets/8b0b13b2-787b-4f5b-ad26-d03e68e35e4d)

AJUSTE DE PERMISOS 
sudo chown -R www-data:www-data /var/www/centro
sudo chmod -R 755 /var/www/centro
![image](https://github.com/user-attachments/assets/212827f9-220e-4866-9996-dba62bfd3c49)

Configurar la aplicación Python
Crea el archivo /var/www/departamentos/app.wsgi
def application(environ, start_response):
    status = '200 OK'
    output = b"Aplicación Python funcionando correctamente."
    
    response_headers = [('Content-type', 'text/plain'),
                        ('Content-Length', str(len(output)))]
    start_response(status, response_headers)
    return [output]
Ajusta permisos
![image](https://github.com/user-attachments/assets/3632a513-26fa-495a-a510-e7d19a458451)


Paso 2:Activar los módulos necesarios para ejecutar php y acceder a mysql
Instalar PHP y extensiones:
![image](https://github.com/user-attachments/assets/a7204fa9-4c2b-43a3-851e-b95d6470c151)

Activar el módulo de PHP:
![image](https://github.com/user-attachments/assets/f33a64fc-bdb2-4c55-a410-0773054fae9e)

paso 3:Instala y configura wordpress

Configurar MySQL para WordPress
instalamos mysql server
![image](https://github.com/user-attachments/assets/9d859992-a1ef-4937-a32c-dba454929a15)

 Configurar el archivo de Apache para WordPress
Crear el directorio para WordPress:
![image](https://github.com/user-attachments/assets/390e9200-c453-4d69-a361-df796f1e9cfe)

Dar permisos adecuados:
![image](https://github.com/user-attachments/assets/d002a39b-b4ec-42ce-8680-9db797655465)

Habilitar el sitio y los módulos necesarios:
![image](https://github.com/user-attachments/assets/8eb11a0b-bb5d-4a1b-a7fa-dcd91cfc1cae)

configuramos wordpress
Configurar el archivo wp-config.php:
Editar wp-config.php:
![image](https://github.com/user-attachments/assets/126b1ffb-3985-4238-9f16-05f048366bb5)


accedemos a la pagina http
![image](https://github.com/user-attachments/assets/bff80335-9f6f-4f94-a9fe-41cd75ebdbe6)

Crea y despliega una pequeña aplicación Python para comprobar que funciona correctamente.

Crear la aplicación Python
Crea un directorio para tu aplicación Python: 
![image](https://github.com/user-attachments/assets/452c0983-912a-4b0c-a2e5-b93b374e8701)

Dentro de este directorio, crea un archivo Python para tu aplicación. Por ejemplo, vamos a crear una sencilla aplicación "Hola Mundo": 
![image](https://github.com/user-attachments/assets/e989789d-e0ac-4b09-8e8d-8499195e1263)
![image](https://github.com/user-attachments/assets/847632c1-9449-4ae7-a6bb-8b1d21b8f0b3)

Configurar Apache para la aplicación Python
Crea un archivo de configuración para el sitio: 
Agregue la siguiente configuración al archivo:
![image](https://github.com/user-attachments/assets/d1cbb19d-e035-4d65-8f89-52726a87b833)

 Habilitar el sitio y los módulos necesarios 
Habilita el nuevo sitio y el módulo mod_wsgi:
![image](https://github.com/user-attachments/assets/162921b3-4e2b-46b5-96d0-75989defa8f8)

Reinicia Apache para aplicar los cambios:
Acceder a la aplicación
![image](https://github.com/user-attachments/assets/7389ce68-5684-4ffe-adc5-bcacf66b64f4)




protegeremos el acceso a la aplicación Python mediante autenticación
Instalar apache2-utils(si aún no está instalado)
![image](https://github.com/user-attachments/assets/ff00586d-b9b4-46c6-8b0e-50fbc9c0ae45)

Crear el archivo.htpasswd
![image](https://github.com/user-attachments/assets/b08bcdf8-a0ec-4f1e-b54c-ac012c944372)

Configurar Apache para utilizar la autenticación
Abra el archivo de configuración de Apache para su aplicación ( departamentos.centro.intranet.conf)

![image](https://github.com/user-attachments/assets/cf96c5bc-14a6-4f6c-a8b6-e79c7b827920)

    • Instala y configura awstat.

. Instalar AWStats

Crear un archivo de configuración para cada dominio:
![image](https://github.com/user-attachments/assets/73656cea-18dc-4d96-b216-5c494f02237e)

Modificamos las siguientes líneas en el archivo de configuración:
LogFile="/var/log/apache2/access.log"
SiteDomain="midominio.net"
HostAliases="midominio.net localhost 127.0.0.1"
AllowToUpdateStatsFromBrowser=1

Generar las estadísticas iniciales:

![image](https://github.com/user-attachments/assets/2bc8212a-8115-4fca-8186-b9028b55ecee)

Crear un archivo de configuración para Apache y awstats:
![image](https://github.com/user-attachments/assets/6e4b4a69-7cc6-4066-9753-0bca5e07297a)

y añadimos las siguientes lineas:
![image](https://github.com/user-attachments/assets/ab0522d0-2bee-4981-a6c2-5695242f5ac0)

Activar la configuración:
![image](https://github.com/user-attachments/assets/742dabec-0fe1-42c9-a007-2f4950e81b2a)

Instala un segundo servidor de tu elección (nginx, lighttpd) bajo el dominio “servidor2.centro.intranet”. Debes configurarlo para que sirva en el puerto 8080 y haz los cambios necesarios para ejecutar php. Instala phpmyadmin.
Instalar Nginx:

![image](https://github.com/user-attachments/assets/fc30453c-9a08-421d-ba93-b1d6b92f8d81)

Crea un nuevo archivo de configuración para el sitio:
![image](https://github.com/user-attachments/assets/6a6568b5-116d-4927-a8f4-05bc4e4af964)

agregamos la siguiente configuración:
![image](https://github.com/user-attachments/assets/5135a2aa-2212-483d-8e41-b75319599aff)

Crea un enlace simbólico para habilitar el sitio:
![image](https://github.com/user-attachments/assets/c72779b9-f2b7-40c8-9861-9f4b22287d4a)

Crea el directorio raíz para el sitio:
![image](https://github.com/user-attachments/assets/ae48279a-ea89-4cc1-98d3-37e5afb2be7b)

Instale PHP y los módulos necesarios:
![image](https://github.com/user-attachments/assets/c0ceacf5-b121-4a8e-b308-305d993982b6)

Crea un enlace simbólico para PHPMyAdmin en el directorio del sitio:
![image](https://github.com/user-attachments/assets/2f652221-6646-4359-bb4f-cc83d80acb32)

Verifica la configuración de Nginx:
![image](https://github.com/user-attachments/assets/0b1b4166-e1ba-4706-8670-c5420add3dd1)

Reinicia Nginx:
![image](https://github.com/user-attachments/assets/f929e43e-d93b-4f74-a2ba-15a37c3ecb59)

verificamos con la url http://servidor2.centro.intranet:8080/phpmyadmin  


