# 5.2 Comment utiliser les volumes Docker ?

Les volumes Docker sont un mécanisme essentiel pour persister et gérer les données générées et utilisées par les conteneurs Docker. Contrairement aux données stockées dans les couches d'un conteneur, les volumes sont stockés dans une partie du système de fichiers de l'hôte géré par Docker, séparée des cycles de vie des conteneurs. Cela signifie que les volumes permettent de conserver les données même après la suppression d'un conteneur, facilitant ainsi le partage de données entre conteneurs et la persistance des données importantes.


## 5.2.1 Création et Gestion des Volumes Docker

Les volumes Docker sont utilisés pour persister et partager des données entre les conteneurs et l'hôte. Voici comment gérer les volumes avec les commandes Docker de base :

### 5.2.1.1 Création d'un Volume

**Créer un nouveau volume** :
   ```bash
   docker volume create mon_volume
   ```
   Cette commande crée un volume nommé `mon_volume`. Docker gère ce volume, le stockant dans un répertoire dédié sur l'hôte.

### 5.2.1.2 Lister les Volumes

**Lister tous les volumes existants** :
   ```bash
   docker volume ls
   ```
   Affiche tous les volumes Docker disponibles sur l'hôte, vous permettant de voir `mon_volume` que vous venez de créer, ainsi que tout autre volume existant.

### 5.2.1.3 Inspecter un Volume

**Inspecter les détails d'un volume** :
   ```bash
   docker volume inspect mon_volume
   ```
   Fournit des informations détaillées sur `mon_volume`, y compris le chemin sur l'hôte où les données du volume sont stockées, ce qui est utile pour comprendre comment Docker gère les données de volume en interne.

### 5.2.1.4 Supprimer un Volume

**Supprimer un volume** :
   ```bash
   docker volume rm mon_volume
   ```
   Supprime `mon_volume`. Cette action est définitive et supprime toutes les données stockées dans le volume. Assurez-vous que les données ne sont plus nécessaires avant de supprimer un volume.

### 5.2.1.5 Utiliser un Volume avec un Conteneur

**Démarrer un conteneur avec un volume monté** :
   ```bash
   docker run -d -v mon_volume:/data mon_image
   ```
L'option `-d` signifie "détaché", ce qui permet au conteneur de s'exécuter en arrière-plan. L'option `-v` permet de monter `mon_volume` sur le répertoire `/data` du conteneur, ce qui assure la persistance des données.
Toutes les données écrites par le conteneur dans `/data` seront persistées dans `mon_volume`, même après l'arrêt ou la suppression du conteneur.

Ces commandes de base constituent le fondement de la gestion des volumes dans Docker, offrant une méthode simple mais puissante pour gérer la persistance des données dans les environnements conteneurisés. En partant de ces commandes, vous pouvez progressivement explorer des utilisations plus avancées des volumes, comme partager des données entre plusieurs conteneurs ou utiliser des volumes pour des bases de données, comme illustré précédemment.



### 5.2.2 Monter un Volume dans un Conteneur Docker

Après avoir vu comment gérer les volumes dans Docker, il est essentiel de comprendre comment utiliser ces volumes pour la persistance des données dans des applications spécifiques. Cela est particulièrement important pour les applications qui nécessitent un stockage durable, comme les bases de données ou les applications web avec des fichiers statiques.

#### Exemple Pratique : Persistance de Données pour une Base de Données

1. **Base de Données SQLite** :
   - Utiliser un volume Docker permet de s'assurer que la base de données SQLite reste intacte même après la suppression ou la recréation du conteneur.
   - **Exemple de commande** :
     ```bash
     docker run -d -v mon_volume:/db mon_image_sqlite
     ```
     Cette commande lance un conteneur avec une application utilisant SQLite, montant `mon_volume` sur le répertoire `/db` du conteneur, ce qui assure la persistance des données de la base de données SQLite.

2. **Base de Données PostgreSQL** :
   - Pour une base de données comme PostgreSQL, qui stocke ses données dans un répertoire spécifié, utiliser un volume Docker assure la persistance des données entre les redémarrages du conteneur ou les mises à jour de l'image.
   - **Exemple de commande** :
     ```bash
     docker run -d -v mon_volume:/var/lib/postgresql/data postgres
     ```
        - `docker run` : C'est la commande pour créer et démarrer un nouveau conteneur Docker.
        - `-d` : Cette option signifie "détaché" et indique à Docker d'exécuter le conteneur en arrière-plan. Cela permet à l'utilisateur de continuer à utiliser le terminal pour d'autres commandes pendant que le conteneur s'exécute.
        - `-v mon_volume:/var/lib/postgresql/data` : Cette option spécifie un montage de volume. Elle indique à Docker de monter le volume nommé `mon_volume` dans le système de fichiers du conteneur à l'emplacement `/var/lib/postgresql/data`. C'est le répertoire où PostgreSQL stocke ses données, permettant ainsi la persistance des données de la base de données entre les redémarrages ou mises à jour du conteneur.
        - `postgres` : C'est le nom de l'image Docker à utiliser pour créer le conteneur. Dans ce cas, `postgres` fait référence à l'image officielle PostgreSQL disponible sur Docker Hub. Cette image contient tout le nécessaire pour exécuter un serveur PostgreSQL, incluant le logiciel PostgreSQL lui-même et les configurations de base. Lorsque vous spécifiez simplement `postgres`, Docker va chercher cette image sur Docker Hub (ou dans votre cache local d'images, s'il l'a déjà téléchargée auparavant) et l'utilisera pour créer le conteneur.

En résumé, cette commande lance un conteneur PostgreSQL en arrière-plan, utilise un volume pour la persistance des données de la base de données, et se base sur l'image officielle PostgreSQL de Docker Hub.

### Avantages de l'Utilisation des Volumes pour les Bases de Données

- **Persistance des Données** : Les volumes garantissent que les données restent sauvegardées en dehors du conteneur, préservant vos données lors des mises à jour ou suppressions de conteneurs.
- **Performance** : Les volumes peuvent offrir un accès plus rapide aux données comparé aux couches d'écriture du conteneur.
- **Sécurité** : La gestion et la sauvegarde indépendantes des volumes apportent une couche supplémentaire de sécurité pour les données sensibles.

Cette section démontre comment monter un volume dans un conteneur Docker pour assurer la persistance des données, offrant ainsi un guide pratique sur l'importance des volumes dans la gestion des données avec Docker.
