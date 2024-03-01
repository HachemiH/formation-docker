# TP 7 : Docker Compose

Ce TP est à réaliser sur votre machine en local.

1. Créer un dossier `back-end` sur votre disque.
2. Créer un fichier `docker-compose.yml`, ce fichier doit :
   1. Démarrer un conteneur `postgres` :
      1. Définir les variables d'environnement relatives à PostgreSQL.
      2. Définir le port du conteneur.
      3. Définir le volume utilisé par le conteneur.
      4. Définir le réseau auquel sera relié le conteneur.
   2. Créer un volume `pgdata`. 
   3. Créer un réseau `app-network`.