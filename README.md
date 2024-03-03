# 4. Lancer le build de l'image avec le tag ``nest-api:1.0``.

Pour monter `build` l'image de l'application, il suffit d'exécuter la commande `docker build`, suivi du nom ainsi que du tag de l'image et enfin du chemin d'accès de cette dernière.

![](./assets/cli.png)

- `docker build` : Permet de dire à Docker que nous voulons créer une image.
- `-t` : Permet de spécifier le nom ainsi que le tag de l'image.
  - `nest-api`: Le nom de l'image
  - `:1.0` : Le tag de l'image
- `app/` : Le chemin d'accès pour lancer le build (le répertoire dans lequel se trouve le DockerFile)