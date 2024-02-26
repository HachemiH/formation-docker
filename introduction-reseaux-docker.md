# 6.1 Réseautage dans Docker : Introduction et Fondamentaux

Le réseautage dans Docker est un élément clé pour permettre la communication entre les conteneurs ainsi qu'entre les conteneurs et le monde extérieur. Cette capacité est essentielle pour le fonctionnement efficace et sécurisé des applications conteneurisées.

## 6.1.1 Qu'est-ce que le Réseautage dans Docker ?

Le réseautage dans Docker désigne l'ensemble des fonctionnalités qui permettent aux conteneurs de communiquer entre eux et avec d'autres réseaux. Docker propose plusieurs stratégies de réseau pour gérer ces interactions, chacune adaptée à des cas d'usage spécifiques.

## 6.1.2 Importance du Réseautage

- **Isolation et Sécurité** : Fournit une isolation entre conteneurs, renforçant la sécurité de l'application.
- **Connectivité** : Permet aux conteneurs de fonctionner ensemble comme un système cohérent et d'accéder à des ressources externes.
- **Flexibilité** : Offre différentes options de réseau adaptées aux besoins de performance, d'isolation ou de communication entre hôtes.

## 6.1.3 Concepts de Base

### Types de Réseaux dans Docker

- **Bridge** : Utilisé pour la communication entre conteneurs sur le même hôte.
- **Host** : Pour des performances maximales en attachant directement le conteneur à l'hôte.
- **Overlay** : Facilite la communication entre conteneurs sur différents hôtes, important pour les applications distribuées.
- **Macvlan** : Donne une adresse MAC unique à chaque conteneur, les faisant apparaître comme des dispositifs physiques sur le réseau.

### Choix du Type de Réseau

Le choix dépend des besoins en termes de sécurité, performance, et architecture de l'application. Chaque type de réseau offre des avantages spécifiques selon le contexte d'utilisation.

## Exemple Pratique : Serveur Web Nginx et API Backend

Illustrons l'importance du réseautage avec un exemple d'application composée d'un serveur web Nginx et d'une API backend, nécessitant une communication inter-conteneur.

### Création d'un Réseau Docker

```bash
docker network create mon_reseau
```
- **`docker network create`** : Crée un nouveau réseau.
- **`mon_reseau`** : Nom du réseau créé.

### Démarrage de l'API Backend

```bash
docker run -d --name api_backend --network mon_reseau mon_image_api
```
- **`-d`** : Mode détaché pour exécuter le conteneur en arrière-plan.
- **`--name`** : Nomme le conteneur `api_backend`.
- **`--network`** : Connecte le conteneur au réseau `mon_reseau`.

### Démarrage du Serveur Web Nginx

```bash
docker run -d --name mon_nginx --network mon_reseau -p 80:80 nginx
```
- **`-p 80:80`** : Mappe le port 80 du conteneur sur le port 80 de l'hôte.

Cet exemple démontre comment Nginx peut servir du contenu statique tout en redirigeant certaines requêtes vers l'API backend, le tout au sein d'un réseau Docker isolé. Cela souligne l'importance de comprendre et de configurer correctement le réseautage dans Docker pour le développement d'applications modernes et distribuées.
