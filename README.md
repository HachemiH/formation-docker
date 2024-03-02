# 4. Vérifier que le volume `pgdata` est bien utilisé par le conteneur.

Pour vérifier que le conteneur utilise bien le volume `pgdata`, il suffit d'éxecuter la commande `docker inspect` suivi du nom ou de l'ID du conteneur :

![](./assets/cli.png)

Et de chercher la section `Mounts` :

![](./assets/cli-2.png)

Ici, on voit que la section `Mounts` contient une entrée :

- `Type: Volume` : Le type de mount est un Volume.
- `Name: pgdata` : Le nom du Volume.
- `Destination: /var/lib/postgresql/data` : Le chemin d'accès dans le conteneur.