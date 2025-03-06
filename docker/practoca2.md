mostramos el hello word como en la practica 1
![image](https://github.com/user-attachments/assets/f2a86546-27fe-4885-9ce3-40cfb4d69a3b)
para mostrar imagenes es :

sudo docker images
![image](https://github.com/user-attachments/assets/c0faef19-ffe1-4283-a2c5-5a933e57bea8)
mostrar contenedores:
sudo docker ps
![image](https://github.com/user-attachments/assets/a615829a-2a31-4651-9433-6d1dd791ba71)
creamos el docker file
mkdir mi_proyecto
cd mi_proyecto
nano Dockerfile
![image](https://github.com/user-attachments/assets/978eeef4-d2bf-48cc-9345-766037b9bb44)
metemos la configuracion en el dockerfile

# Indica la imagen base
FROM ubuntu:latest

# Actualiza paquetes e instala, por ejemplo, curl
RUN apt-get update && apt-get install -y curl

# Mensaje o comando que se ejecutará por defecto
CMD ["echo", "Hola desde mi contenedor!"]

![image](https://github.com/user-attachments/assets/9b2a0e83-df91-49df-90ba-cd5ba2dcc81e)
montamos el proyecto

docker build -t proyecto .
![image](https://github.com/user-attachments/assets/4ff6e9a1-02d8-4f40-bc84-6e28e5594a02)
corremos la imagen 
docker run proyecto
![image](https://github.com/user-attachments/assets/0b43603a-88f9-4058-bdcd-7812c86f5d1f)

creamos cuenta de hub.docker.com
![image](https://github.com/user-attachments/assets/d960e793-8dda-4230-9d63-ae4a1047cac1)
creamos el repositorio
![image](https://github.com/user-attachments/assets/26811ba2-fd44-48ae-8801-7876d1d676b2)
hacemos login 
![image](https://github.com/user-attachments/assets/327488d6-6981-4cbc-ad94-02bd7b85ecca)
iniciamos la soguiente imagen
docker tag proyecto javiersand2/proyecto:latest
subimos el contenedor
docker push javiersand2/proyecto:latest
  y subimos elk contenedor a docker
  ![image](https://github.com/user-attachments/assets/4f25edd5-8143-4c37-866a-527620bfe8c2)

  
