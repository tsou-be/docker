# leçons Docker
## Commandes De base
# Commandes Docker de Base

## 1. Gestion des images

 ```
- docker pull <image>
```  
  Télécharger une image depuis un registre (ex: Docker Hub).

- ```
- docker images
- ```
  Lister les images Docker locales.

 ```
- docker rmi <image
``` 
  Supprimer une image Docker locale.

## 2. Gestion des conteneurs

 ```
- docker run <image>
```  
  Lancer un nouveau conteneur à partir d’une image.

```
- docker run -it <image> /bin/bash
```
  Lancer un conteneur en mode interactif avec un terminal.

 ```
- docker ps
``` 
  Lister les conteneurs en cours d’exécution.

 ```
- docker ps -a
``` 
  Lister tous les conteneurs (actifs et arrêtés).

```
docker stop <container_id>
```  
  Arrêter un conteneur en cours.

```
- docker start <container_id>
```  
  Démarrer un conteneur arrêté.

```
docker restart <container_id>
``` 
  Redémarrer un conteneur.

```
docker rm <container_id>
``` 
  Supprimer un conteneur arrêté.

 ```
- docker exec -it <container_id> bash
```  
  Exécuter une commande ou ouvrir un terminal dans un conteneur en cours.

## 3. Gestion des volumes

 ```
- docker volume ls
 ``` 
  Lister les volumes Docker.

 ```
 docker volume create <nom>
``` 
  Créer un volume Docker.

 ```
 docker volume rm <nom>
``` 
  Supprimer un volume Docker.

## 4. Gestion des réseaux

```
- docker network ls
```  
  Lister les réseaux Docker.

 ```
 docker network create <nom>
``` 
  Créer un réseau Docker.

```
docker network rm <nom>
```  
  Supprimer un réseau Docker.

## 5. Docker Compose (gestion multi-conteneurs)

```
- docker-compose up
``` 
  Lancer tous les services définis dans un fichier `docker-compose.yml`.

 ```
- docker-compose down
``` 
  Arrêter et supprimer les conteneurs, réseaux créés par Docker Compose.


  # Résumé des composants de Docker

---

##  1. Dockerfile

**Définition :**  
Un Dockerfile est un fichier texte contenant des instructions permettant de construire une **image Docker personnalisée**.

**Exemple :**
```
Dockerfile
FROM python:3.10-slim
COPY app.py /app/
WORKDIR /app
RUN pip install flask
CMD ["python", "app.py"]
```


# Docker Volume & Network - Résumé


##  Docker Volume

**Définition :**  
Un volume Docker est un mécanisme de stockage persistant utilisé pour conserver les données même après la suppression d’un conteneur.

**Commandes utiles :**

###Créer un volume
```
docker volume create mon_volume
```

# Lister les volumes
```
docker volume ls
```
# Supprimer un volume
```
docker volume rm mon_volume
```

# Utiliser un volume dans un conteneur
```
docker run -v mon_volume:/app/data myimage
```
