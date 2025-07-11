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

