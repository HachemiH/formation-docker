# 7.2 Comment démarrer et arrêter des services avec Docker Compose ?

## Démarrer les Services

- **Pour lancer tous les services** définis dans votre `docker-compose.yaml` :
  ```bash
  docker-compose up
  ```
- **En arrière-plan** :
  ```bash
  docker-compose up -d
  ```

## Arrêter les Services

- **`docker-compose stop`** : Arrête les services sans les supprimer, permettant un redémarrage rapide.
- **`docker-compose down`** : Arrête et supprime les conteneurs, réseaux, et volumes anonymes créés par `up`.

## Redémarrer les Services

- **Redémarrer tous les services** ou un service spécifique :
  ```bash
  docker-compose restart [service_name]
  ```
    Remplacez [service_name] par le nom du service à redémarrer. Omettez [service_name] pour redémarrer tous les services.

## Voir les Logs

- **Consulter les logs** de tous les services :
  ```bash
  docker-compose logs
  ```
- **En temps réel** :
  ```bash
  docker-compose logs -f
  ```

## Exemples Pratiques

### Démarrage en Arrière-Plan

Pour démarrer l'API et le serveur Nginx en arrière-plan, utilisez :

```bash
docker-compose up -d
```

### Arrêter Sans Supprimer

Si vous souhaitez arrêter l'API et le serveur Nginx sans les supprimer pour un redémarrage rapide :

```bash
docker-compose stop
```

Cette structure clarifie les commandes essentielles pour gérer le cycle de vie des services Docker Compose, incluant des exemples pour illustrer l'utilisation pratique de ces commandes.
