# 2. Démarrer un conteneur nommé `my-database` de l'image `postgres` (Volume)

Pour créer un conteneur de l'image `postgres`, il suffit de paramètrer le conteneur avant de le lancer en cliquant sur `Optional Settings`.

![](./assets/dd.png)

Et de remplir les informations du conteneur.

![](./assets/dd-2.png)

- `Container name` : Le nom du conteneur, ici `my-database`.
- `Host Port` : Le port d'entré du conteneur, lorsqu'une requête arrive sur le port `5432` de l'hôte, il est redirigé vers le port `5432` du conteneur (`5432` étant le port de PostgreSQL).
- `Host path` : Le chemin d'accès du volume `pgdata`, ici, il suffit d'utiliser le nom du volume que nous avons créer précédement, pour que Docker définisse le chemin d'accès du volume de l'hôte.
- `Container path` : Le chemin d'accès où les données seront stockès, ici dans le cadre de PostgreSQL, il s'agit du chemin `/var/lib/postgresql/data` dans le conteneur.
- `Variables d'environnement` : Les variables d'environnement nécessaires au lancement d'un conteneur Postgres