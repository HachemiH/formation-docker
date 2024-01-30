# 3.3 Commandes de Base pour Gérer les Images Docker

## Introduction
Docker permet de créer, gérer et utiliser des images, qui sont des modèles pour les conteneurs Docker. Les commandes de base pour travailler avec ces images sont essentielles pour tout développeur souhaitant utiliser Docker efficacement.

## Commandes Essentielles pour les Images Docker

### Lister les Images Docker
Pour voir toutes les images Docker disponibles sur votre système, utilisez la commande :

- `docker images`

Cette commande affiche une liste de toutes les images Docker stockées localement, avec des détails tels que le tag, la taille et l'ID de l'image.

### Télécharger une Image depuis Docker Hub
Pour télécharger une image depuis Docker Hub, utilisez la commande :

- `docker pull [nom_de_l'image]`

Remplacez `[nom_de_l'image]` par le nom de l'image que vous souhaitez télécharger. Par exemple, `docker pull ubuntu` téléchargera la dernière version de l'image Ubuntu.

### Supprimer une Image
Si vous souhaitez supprimer une image Docker de votre système, utilisez :

- `docker rmi [ID_de_l'image]`

Remplacez `[ID_de_l'image]` par l'ID de l'image que vous souhaitez supprimer. Vous pouvez trouver l'ID de l'image en utilisant la commande `docker images`.



#### Comment pousser une image vers un registre Docker ?
- `docker push [OPTIONS] NAME[:TAG]`

Exemple :
Supposons que vous avez une image Docker appelée `monapp` avec un tag `v1.0`, et vous souhaitez la pousser vers Docker Hub. La commande serait :

- `docker push monapp:v1.0`

Cette commande va pousser l'image `monapp` avec le tag `v1.0` vers votre registre sur Docker Hub. Assurez-vous que vous êtes connecté à Docker Hub dans votre terminal et que vous avez les droits nécessaires pour pousser l'image dans le registre.

Assurez-vous d'abord de vous connecter à Docker Hub et de taguer votre image avec votre nom d'utilisateur Docker Hub.

## Création d'Images Personnalisées
La création d'images personnalisées implique l'utilisation de Dockerfile et d'autres commandes avancées. Ce sujet, un peu plus complexe, sera expliqué en détail dans une section dédiée plus tard dans cette formation.
