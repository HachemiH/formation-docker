# 8. Vérifier que le dossier `/app/data` contient le fichier `test.md`.

Pour vérifier que le fichier `test.md` existe bien dans le dossier `/app/data`, il suffit d'exécuter la commande `docker exec -it` suivi du nom du conteneur ainsi que le shell à utiliser. 

![](./assets/cli.png)

Puis de naviguer dans le dossier `/app/data` et de lister les fichiers à l'aide de la commande `ls`.

Ici, on voit que le fichier `test.md` existe bien dans le dossier `/app/data` du conteneur.