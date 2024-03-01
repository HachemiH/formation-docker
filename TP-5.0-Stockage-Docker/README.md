# TP 5 : Stockage dans Docker

Avant de vous lancer dans ce TP, veillez à récupérer l'image `postgres` sur votre machine.

# Partie 1 : Avec Docker Desktop

1. Créer un volume nommé `pgdata`
2. Créer un conteneur nommé `my-database` de l'image `postgres`.
   1. Lier le volume `pgdata`, le chemin d'accès dans le conteneur doit être `/var/lib/postgresql/data`.
   2. Ajouter les variables d'environnement nécessaire au lancement du conteneur.
3. Vérifier que le volume `pgdata` est bien utilisé par le conteneur via l'onglet des volumes.
4. Vérifier que le volume `pgdata` est bien utilisé par le conteneur via les onglets du conteneur.
5. Créer un dossier `my-datas` sur votre disque.
6. Créer un conteneur nommé `my-nginx` de l'image `nginx`.
   1. Líer le dossier `my-datas` sur votre disque au chemin `/app/data` du conteneur.
7. Créer un fichier `test.md` dans le dossier `my-datas` sur votre disque.
8. Vérifier que le dossier `/app/data` contient le fichier `test.md` via l'onglet du conteneur dans Docker Desktop.