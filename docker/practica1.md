practica 1 Instalacion de docker
limpiamos la maquinas de paqketes que den problemas con docker:for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
![image](https://github.com/user-attachments/assets/5789063c-66b2-47f7-9dba-c2a97f4db4c8)

realizar setup para docker
sudo apt-get update
sudo apt-get install ca-certificates curl
![image](https://github.com/user-attachments/assets/f6a672c5-a938-445f-9121-6964cf578d9c)

sudo install -m 0755 -d /etc/apt/keyrings

sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc
añadimos el repositorio en el apt
![image](https://github.com/user-attachments/assets/ead15c89-5ad4-451b-9d3b-d8022823eb85)
instalamos los paquetes de docker :
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
![image](https://github.com/user-attachments/assets/29622c47-6993-43ea-ad9b-8c3a06614e55)
lo probamos 
sudo docker run hello-world
![image](https://github.com/user-attachments/assets/8938d06f-775e-4f9e-841a-b2921fa49130)
