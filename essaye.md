# leçons Docker
## Commandes De base

***1. Gestion des images***

```
docker pull <image>
```
Télécharger une image depuis un registre (ex: Docker Hub)
```
    docker images
```
    Lister les images Docker locales. 
```
    docker rmi <image>
```
   Supprimer une image Docker locale.

Construire une image
``` 
docker build -t mon-app . 

```
Lancer un conteneur en mode détaché
```
docker run -d -p 3000:3000 --name mon-conteneur mon-app
```

**Voir les logs**
```
docker logs mon-conteneur
```

**Entrer dans un conteneur en cours d'exécution**
```
docker exec -it mon-conteneur sh
```

## docker volume
1.comment créer un volume
```
docker volume ls 

```

```
docker volume create mynginx 
```

```
docker volume ls 
```
2.lancer de conteneur
```
docker run -d --name mon-conteneur nginx 
```
  ## dockerfile 
*créer dockerfile* 
```
nano Dockerfile

```

metre un code dans dockerfile

avant tout,
``` sudo usermod -aG docker $USER ```
``` newgrp docker ``` ou déconnecter et reconnecter
*les tailles de l'image*
```
docker history monimage:v1.0
 ```
``` 
docker run -tid --name test monimage:v1.0

```
``` 
docker exec -ti test bash
```

# Docker network 
## Créer réseau 
```
docker network create mon_reseau

```
*pour verifié*
```
docker network create mon_reseau
```

## Lancer un conteneur nginx dans le réseau 
```
docker run -d --name web --network mon_reseau nginx
```
*pour verifié:

```
docker run -d --name web --network mon_reseau nginx
```

## Lancer un conteneur client dans le même réseau
```
docker run -it --rm --name client --network mon_reseau alpine sh
```

*puis dans le shell du conteneur client, tape :*
```
ping web

```

##  Nettoyage
```
docker stop web
docker rm web
docker network rm mon_reseau
```
## Résumé 
```
docker network create mon_reseau
docker run -d --name web --network mon_reseau nginx
docker run -it --rm --name client --network mon_reseau alpine sh
```
# Docker compose
**créer un dossier**
```
mkdir exercice-compose
cd exercice-compose
```
## 1. Créer le fichier docker-compose.yml

***lancer les services***
```
docker-compose up -d
```

## 2. Arrêter et supprimer les conteneurs
```
docker-compose down

```

