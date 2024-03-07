# 3. Démarrer un conteneur nommé `my-database` de l'image `postgres`. (Volume)

Pour démarrer un conteneur `postgres` il suffit d'exécuter la commande `docker run`.

![](./assets/cli.png)

- `docker run` : La commande Docker pour démarrer un conteneur.
- `--name` : Définit le nom du conteneur.
- `-e` : Définit une variable d'environnement (ici `POSTGRES_USER=demo`, `POSTGRES_PASSWORD=test`)
- `-p` : Définit le port de l'hôte (ici `5432` vers le port `5432` du conteneur)
- `-v` : Définit le volume utilisé par le conteneur.
  - `pgdata` : Le nom du volume à utiliser
  - `:` : Sert à définir le chemin d'accès dans le conteneur
  - `/var/lib/postgresql/data` : Le chemin d'accès dans le conteneur.
- `postgres` : L'image à partir de laquelle le conteneur doit démarrer.