# 14. Supprimer l'image nginx proprement.

Si vous tentez de supprimer l'image `nginx` avec la commande `docker rmi nginx`, un message d'erreur s'affichera.

![](./assets/shell.png)

Pour régler l'erreur, il suffit d'éteindre le conteneur et le supprimer :

![](./assets/shell-2.png)

Et réexécuter la commande de suppression :

![](./assets/shell-3.png)