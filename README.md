# 7. Consulter les informations détaillées du conteneur `postgres`.

Pour consulter les informations du conteneur il suffit d'exécuter la commande `docker inspect` suivi du nom ou de l'ID du conteneur.

![](./assets/cli.png)

On peut voir dans la section `Networks` du conteneur qu'il est connecté au réseau `production-network`