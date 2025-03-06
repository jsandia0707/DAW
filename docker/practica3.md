descargamos la imagen de ubuntu
![image](https://github.com/user-attachments/assets/0d3c83b3-3fee-4279-80d1-da1dd79198a6)

ahora el hola mundo
![image](https://github.com/user-attachments/assets/753d800d-a243-437b-8848-f27ded1a2adf)
ahora la imagen ngix
![image](https://github.com/user-attachments/assets/e8e59794-449d-428b-9f51-15bef4737dac)

listado de imagenes
![image](https://github.com/user-attachments/assets/ff58ec24-4c57-4274-a84e-e75fbd85c0dd)
ejecutamos el contenedor y lo nombramos
docker run --name myhello1 hello-world
![image](https://github.com/user-attachments/assets/80f4f9ac-30fe-4756-8b6a-ac016a25c36c)
LO MISMO PARA HELLO WORDL
docker run --name myhello1 hello-world
![image](https://github.com/user-attachments/assets/f438bfe8-2152-4760-85c6-10758ba48b09)
volvemos a ver los contenedores 
![image](https://github.com/user-attachments/assets/92fd50f2-cf4b-46ea-a951-99e571a6ade8)

paramos las imagenes 
docker stop myhello1
docker stop myhello2
docker stop myhello3
borramos los contenedores
docker rm myhello1
docker rm myhello1
docker rm myhello1
los volvemos a mostrar
![image](https://github.com/user-attachments/assets/2eeea07f-f0e1-492e-a93c-7326dc46154a)
para borrar todos docker rm -f $(docker ps -aq)

