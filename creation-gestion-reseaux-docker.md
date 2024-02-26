# 6.2 Création et Gestion des Réseaux Docker 

L'utilisation des réseaux Docker permet de faciliter et de sécuriser la communication entre les conteneurs, comme illustré dans cet exemple avec un serveur Nginx (agissant comme serveur frontend) et une API backend. Voici comment procéder à la création, la gestion et l'utilisation des réseaux Docker pour orchestrer la communication entre conteneurs.

## Création d'un Réseau Docker

Tout d'abord, créez un réseau Docker personnalisé qui servira de pont pour la communication entre le conteneur Nginx et le conteneur de l'API backend.

```bash
docker network create --driver bridge mon_reseau
```

- **`--driver bridge`** : Spécifie que le réseau utilise le driver bridge, idéal pour créer un réseau local permettant la communication entre conteneurs sur le même hôte Docker.

## Listing des Réseaux Disponibles

Pour voir tous les réseaux Docker disponibles sur votre système, utilisez :

```bash
docker network ls
```

Cette commande liste tous les réseaux créés, y compris le réseau par défaut et ceux que vous avez créés.

## Déploiement des Conteneurs sur le Réseau

### Déploiement de l'API Backend

Lancez le conteneur de l'API backend en le connectant au réseau `mon_reseau`.

```bash
docker run -d --name api_backend --network mon_reseau mon_image_api
```

### Déploiement de Nginx comme Serveur Frontend

Pour le serveur Nginx, faites de même en le connectant au réseau pour qu'il puisse communiquer avec l'API backend.

```bash
docker run -d --name nginx_frontend --network mon_reseau -p 80:80 nginx
```

- **Comprendre `-p 80:80` avec l'Analogie d'une Adresse Postale** :

Imaginez que vous expliquez à quelqu'un comment trouver un appartement spécifique dans un immeuble situé au "6/3 rue du Boulevard". Ici, "6" pourrait représenter le numéro de l'immeuble dans la rue, et "3" l'appartement spécifique dans cet immeuble. En Docker, quand vous utilisez `-p 80:80`, c'est similaire :
    - Le premier "80" est comme le numéro de l'immeuble ("6" dans notre analogie d'adresse), le port sur votre machine hôte. C'est la "rue" par laquelle les requêtes arrivent à votre système.
    - Le second "80", séparé par `:`, est comme le numéro de l'appartement ("3" dans notre analogie), le port à l'intérieur du conteneur. C'est la destination finale de la requête une fois qu'elle est entrée dans l'immeuble.

Ainsi, `-p 80:80` peut être interprété comme "pour atteindre cet appartement spécifique (le service dans le conteneur), commencez par venir à l'immeuble numéro 80 (le port de l'hôte) sur la rue du Boulevard (votre ordinateur), puis dirigez-vous vers l'appartement numéro 80 à l'intérieur (le port du conteneur)."

Cette analogie vise à clarifier le mappage des ports en Docker, facilitant la compréhension de comment les requêtes externes sont acheminées du monde extérieur vers une application spécifique exécutée dans un conteneur.

## Suppression d'un Réseau

Si vous souhaitez supprimer le réseau créé (après avoir arrêté et supprimé les conteneurs y étant connectés) :

```bash
docker network rm mon_reseau
```

Cette commande supprime le réseau `mon_reseau`, assumant qu'aucun conteneur n'y est actuellement connecté.

## Pourquoi Utiliser des Réseaux Docker ?

La création de réseaux Docker permet une communication sécurisée et isolée entre les conteneurs, tels que Nginx et une API backend, en fournissant :

- **Isolation** : Les conteneurs sur un réseau personnalisé sont isolés des autres conteneurs non connectés à ce réseau, augmentant ainsi la sécurité.
- **Simplicité de la Configuration** : Les conteneurs peuvent communiquer en utilisant les noms des conteneurs, éliminant le besoin de gérer les adresses IP statiques.
- **Flexibilité** : Permet le déploiement d'architectures de microservices en facilitant la communication entre services de manière sécurisée et isolée.

En intégrant la gestion des réseaux dans votre flux de travail Docker, vous bénéficiez d'une méthode robuste pour orchestrer la communication entre les conteneurs de vos applications, essentielle pour les architectures modernes basées sur les conteneurs.

