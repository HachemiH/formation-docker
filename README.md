# 6. Démarrer un conteneur nommé `my-nginx` de l'image `nginx`

Pour démarrer un conteneur nommé `my-nginx` de l'image `nginx`, il suffit d'exécuter la commande `docker run` :

![](./assets/cli-2.png)

- `docker run` : Sert à dire à Docker que nous voulons lancer un conteneur
- `--name` : Définit le nom du conteneur
- `-p` : Définit la redirection du port de l'hôte vers le port de conteneur (ici port `80` de l'hôte vers le port `80` du conteneur)
- `-v` : Définit que nous allons monter un volume
  - `./my-datas` : Le chemin d'accès du volume
  - `/app/data` : Le chemin d'accès du conteneur
- `nginx` : Le nom de l'image à partir de laquelle on démarre le conteneur.

Ici, Docker déduit que le chemin d'accès (`./my-datas`) ne correspond pas à un volume, il sait donc qu'il s'agit d'un `bind-mount`.

Voici une version plus détaillée pour monter un bind-mount proprement :

![](./assets/cli.png)

- `--mount` : Dit qu'il s'agit d'un montage d'espace de stockage interne au conteneur.
  - `type=bind` : Définit le type de montage (ici `bind`, donc un `bind-mount`)
  - `source=./my-datas` : Définit le chemin d'accès source du bind-mount (Chemin d'accès de l'hôte).
  - `target=/app/data` : Définit le chemin d'accès du bind-mount dans le conteneur.