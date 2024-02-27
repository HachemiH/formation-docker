# 10. Exécuter la même commande en entrant en mode interactif.

Pour entrer en mode interactif dans un conteneur il faut utiliser la commande `docker exec` avec l'option `-it`, suivi du nom ou de l'ID du conteneur et enfin le shell que nous voulons utiliser dans le conteneur, ici `sh` qui est le shell par défaut du conteneur.

![](./assets/shell.png)

Une fois que nous sommes entrés dans le shell du conteneur, il n'y a plus qu'à exécuter la commande `Hello World`.