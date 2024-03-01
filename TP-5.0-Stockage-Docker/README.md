# TP 5 : Stockage dans Docker

Avant de vous lancer dans ce TP, veillez à récupérer l'image `postgres` sur votre machine.

# Partie 1 : Avec Docker Desktop

1. Créer un volume nommé `pgdata`
2. Créer un conteneur nommé `my-database` de l'image `postgres`.
   1. Lié le volume `pgdata`, le chemin d'accès dans le conteneur doit être `/var/lib/postgresql/data`.
   2. Ajouter les variables d'environnement nécessaire au lancement du conteneur.
3. Vérifier que le volume `pgdata` est bien utilisé par le conteneur via l'onglet des volumes.