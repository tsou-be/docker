# Commandes Docker essentielles

## Construire une image
``` 
docker build -t mon-app . 

```
## Lancer un conteneur en mode détaché
```
docker run -d -p 3000:3000 --name mon-conteneur mon-app
```

## Voir les logs
```
docker logs mon-conteneur
```

## Entrer dans un conteneur en cours d'exécution
```
docker exec -it mon-conteneur sh
```

# docker volume
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
**exemple:
```
docker run -d \
  --name mon-app \
  -p 5000:5000 \
  -e FLASK_ENV=production \
  mon-app-python
```
  # dockerfile
  * créer dockerfile *
    ``` nano Dockerfile ```
mais avant tout ça veiller faire le code suivant :
