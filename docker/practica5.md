ejemplo 1
version: '3.1'
services:
  app:
    container_name: guestbook
    image: iesgn/guestbook
    restart: always
    environment:
      REDIS_SERVER: redis
    ports:
      - 8080:5000
  db:
    container_name: redis
    image: redis
    restart: always
    command: redis-server --appendonly yes
    volumes:
      - redis:/data
volumes:
  redis:
  ![image](https://github.com/user-attachments/assets/0df73d8c-0c54-4c3e-ae69-57eca36b5ec3)
creamos el escenario
![image](https://github.com/user-attachments/assets/dc28ff84-26f1-4493-b1f4-a925d30077b0)
entramoes en el localhost
![image](https://github.com/user-attachments/assets/7a520e66-82b4-4531-a710-fedb857c61ea)
ejemplo 2 repetimos el proceso pàra la pagina temperaturas nano docker-compose.yml


version: '3.1'
services:
  frontend:
    container_name: temperaturas-frontend
    image: iesgn/temperaturas_frontend
    restart: always
    ports:
      - 8081:3000
    environment:
      TEMP_SERVER: temperaturas-backend:5000
    depends_on:
      - backend
  backend:
    container_name: temperaturas-backend
    image: iesgn/temperaturas_backend
    restart: always
    ![image](https://github.com/user-attachments/assets/5a139261-1be8-456c-a5fa-31d7959f45ac)

