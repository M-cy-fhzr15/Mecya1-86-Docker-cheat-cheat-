# Docker-cheat-cheat
# Nom: RAMALALANIAINA 
# Prénoms : Mariucya Mecya 
# N° :186LA/24-25

## Docker “ Commandes de base  

Afficher la version de Docker  
```  
docker version  
```  

Afficher les informations sur Docker  
```  
docker info  
```  

Aide generale  
```  
docker --help  
```  

## Docker Container  

Lister les conteneurs en cours d'exécution 
```  
docker ps  
```  

Lister tous les conteneurs 
```  
docker ps -a  
```  

Lancer un conteneur interactif basée sur Debian  
```  
docker run -it debian bash  
```  

Lancer un conteneur nginx en arrière-plan avec un nom personnalisé  
```  
docker run -d --name serveur_nginx nginx  
```  

Arreter le conteneur serveur_nginx  
```  
docker stop serveur_nginx  
```  

Redemarrer le conteneur serveur_nginx  
```  
docker restart serveur_nginx  
```  

Afficher les logs du conteneur serveur_nginx  
```  
docker logs serveur_nginx  
```  

Executer une commande dans le conteneur serveur_nginx  
```  
docker exec -it serveur_nginx bash  
```  

Supprimer le conteneur serveur_nginx  
```  
docker rm serveur_nginx  
```  

## Docker Image  

Lister les images locales  
```  
docker images  
```  

Telecharger l' image httpd  
```  
docker pull httpd  
```  

Construire une image nommé mon_app  
```  
docker build -t mon_app .  
```  

Taguer l'image pour un depot Docker Hub fictif  
```  
docker tag mon_app monutilisateur/mon_app:v1  
```  

Pousser l'image sur le depot  
```  
docker push monutilisateur/mon_app:v1  
```  

Supprimer une image par son ID  
```  
docker rmi abcdef123456  
```  

## Dockerfile  

```  
nano Dockerfile  
```  

```Dockerfile
FROM node:16
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8080
CMD ["node", "app.js"]
```  

## Docker Compose  

Demarrer les services  
```  
docker-compose up  
```  

Demarrer en arrirre-plan  
```  
docker-compose up -d  
```  

Arrêter et supprimer les conteneurs  
```  
docker-compose down  
```  

Reconstruire les images  
```  
docker-compose build  
```  

Afficher les logs  
```  
docker-compose logs  
```  

Voir l'etat des services  
```  
docker-compose ps  
```  

## Exemple de fichier `docker-compose.yml`  

```yaml
version: '3'
services:
  webserver:
    image: httpd
    ports:
      - "8080:80"
  app:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src/app
```  

## Docker Volumes  

Creer un volume  
```  
docker volume create data_volume  
```  

Lister les volumes  
```  
docker volume ls  
```  

Afficher les dÃ©tails d'un volume  
```  
docker volume inspect data_volume  
```  

Supprimer un volume  
```  
docker volume rm data_volume  
```  

Utiliser un volume dans un conteneur  
```  
docker run -v data_volume:/var/lib/mysql mysql  
```  

## Docker Swarm  

Initialiser un Swarm  
```  
docker swarm init  
```  

Afficher le token pour joindre un worker  
```  
docker swarm join-token worker  
```  

Lister les noeuds du Swarm  
```  
docker node ls  
```  

Creer un service avec 2 replicas  
```  
docker service create --replicas 2 --name app_service httpd  
```  

Lister les services  
```  
docker service ls  
```  

Lister les taches d'un service  
```  
docker service ps app_service  
```  

Deployer une stack  
```  
docker stack deploy -c docker-compose.yml mystack  
```  

Supprimer une stack  
```  
docker stack rm mystack  
```  

## Nettoyage Docker  

Supprimer tous les objets inutilisees  
```  
docker system prune -a  
```  

Supprimer les volumes inutilisees  
```  
docker volume prune  
```  

Supprimer les images non utilisees  
```  
docker image prune  
```
