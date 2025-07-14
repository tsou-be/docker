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
## Créer un réseau Docker
```
docker network create mon_reseau

```
*vérification
```
docker network create mon_reseau
```
**résultat**
  ![Texte alternatif](image.<img width="806" height="190" alt="Capture d’écran du 2025-07-14 15-30-07" src="https://github.com/user-attachments/assets/922ce1bf-ebbe-4031-bece-fde6f7d4ce19" />
jpg)
