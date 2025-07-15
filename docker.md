# apprendre docker 
## Commandes Docker essentielles

**Construire une image**
``` 
docker build -t mon-app . 

```
**Lancer un conteneur en mode détaché** 
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
*exemple:*
```
docker run -d \
  --name mon-app \
  -p 5000:5000 \
  -e FLASK_ENV=production \
  mon-app-python
```
  ## dockerfile avec essaye
*créer dockerfile* 
```
nano Dockerfile

```

metre cet code dans dockerfile:
```

FROM ubuntu:latest
MAINTAINER sitraka
RUN apt-get update \
&& apt-get install -y vim git nano \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

```
mais avant tout ça veiller exécutez la commande suivante :
``` sudo usermod -aG docker $USER ```
et,
``` newgrp docker ``` ou déconnecter et reconnecter
*pour les tailles de l'image*
```
docker history monimage:v1.0
 ```
``` 
docker run -tid --name test monimage:v1.0

```
``` 
docker exec -ti test bash
```
``` 
git

```
``` 
exit

```
``` 
docker rm -f test

``` 
# Docker network 
## a. Créer un réseau Docker
```
docker network create mon_reseau

```
*vérification :
```
docker network create mon_reseau
```
**résultat**

<img width="806" height="190" alt="Capture d’écran du 2025-07-14 15-30-07" src="https://github.com/user-attachments/assets/1e89d6f5-3e3e-47d0-8c17-ef151ac1bd4d" />

## b. Lancer un conteneur nginx dans le réseau 
```
docker run -d --name web --network mon_reseau nginx
```
*vérification :

```
docker run -d --name web --network mon_reseau nginx
```
**résultat**

<img width="805" height="160" alt="Capture d’écran du 2025-07-14 15-47-43" src="https://github.com/user-attachments/assets/8521d5f1-252c-4aba-bb12-ed62559b9138" />

## c.Lancer un conteneur client dans le même réseau
```
docker run -it --rm --name client --network mon_reseau alpine sh
```

*puis dans le shell du conteneur client, tape :*
```
ping web

```
**resultat**
<img width="769" height="142" alt="Capture d’écran du 2025-07-14 16-09-53" src="https://github.com/user-attachments/assets/620529ba-0ce8-4e92-a788-abcfc838e563" />

## d. Nettoyage
```
docker stop web
docker rm web
docker network rm mon_reseau
```
## e. Résumé 
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
*voici un exemple de son contenue*
```
version: '3.8'

services:
  web:
    image: nginx:latest
    container_name: web
    networks:
      - mon_reseau

  client:
    image: alpine:latest
    container_name: client
    command: sh -c "apk add --no-cache curl && sleep 60m"
    networks:
      - mon_reseau
    tty: true
    stdin_open: true

networks:
  mon_reseau:
    driver: bridge

```
***lancer les services***
```
docker-compose up -d
```
**resultat**
<img width="810" height="336" alt="Capture d’écran du 2025-07-14 16-34-04" src="https://github.com/user-attachments/assets/cbe7a7a1-f0e0-4dd5-ba64-89413f0ebd2b" />

## 2. Arrêter et supprimer les conteneurs
```
docker-compose down

```
