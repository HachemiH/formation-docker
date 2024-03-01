# 3.2 Les Registres Docker et Docker Hub

## 3.2.1 Qu'est-ce qu'un Registre Docker ?
Un registre Docker est un service de stockage et de distribution d'images Docker. Il est similaire à une bibliothèque où les images Docker sont les livres, disponibles pour être empruntés (téléchargés) et utilisés.

## 3.2.2 Pourquoi Utiliser un Registre Docker ?
Les registres Docker, comme Docker Hub, offrent un espace centralisé pour stocker et partager des images Docker. Cela facilite le partage d'applications et d'environnements entre différentes équipes ou individus.

## 3.2.3 Docker Hub : Le Registre Docker le Plus Populaire
Docker Hub est le registre public le plus connu et utilisé pour les images Docker. Il propose des images officielles maintenues par des équipes de développement ainsi que des images créées par la communauté.

### 3.2.3.1 Création de Compte et Connexion
Pour utiliser Docker Hub, il est nécessaire de créer un compte. Une fois inscrit, vous pouvez télécharger (pull) des images publiques et télécharger (push) vos propres images.

### 3.2.3.2 Niveaux d'Abonnement
Docker Hub propose différents niveaux d'abonnement :
- **Gratuit** : Permet de télécharger des images publiques et de télécharger un nombre limité d'images privées.
- **Payant** : Offre des options avancées, notamment un nombre plus élevé d'images privées et d'autres fonctionnalités.

## 3.2.4 Tags dans Docker Hub
Les tags dans Docker sont utilisés pour spécifier des versions ou des configurations différentes d'une même image.

### 3.2.4.1 Comment Taguer une Image ?
Pour taguer une image, utilisez la commande `docker tag`. Par exemple :
```
docker tag mon_apache mon_utilisateur/mon_apache:version1
```
Cela crée un tag `version1` pour l'image `mon_apache`.

### 3.2.4.2 Gestion des Tags sur Docker Hub
Sur Docker Hub, les tags aident à organiser et à identifier différentes versions d'une image. Vous pouvez avoir plusieurs tags pour une même image, facilitant ainsi le suivi des versions.

## 3.2.5 Lier le Terminal au Compte Docker Hub
Pour lier votre terminal à votre compte Docker Hub, vous devez vous connecter via la commande `docker login`. Cela permet de pousser et de tirer des images depuis votre compte Docker Hub.

## 3.2.6 Exemples de Registres Docker Connu
- Docker Hub (https://hub.docker.com)
- Google Container Registry (https://cloud.google.com/container-registry)
- Amazon Elastic Container Registry (https://aws.amazon.com/ecr/)

Pour plus d'informations et de guides pratiques sur l'utilisation de Docker Hub, veuillez consulter la [documentation officielle de Docker Hub](https://docs.docker.com/docker-hub/).
