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

##### Exemple Pratique avec SQLite

**Scenario** : Vous souhaitez exécuter une application web simple qui utilise une base de données SQLite pour stocker des données. Pour s'assurer que ces données restent persistantes entre les redémarrages du conteneur, vous utilisez un volume Docker.

1. **Création d'un Volume** : Commencez par créer un volume Docker où vos données de base de données seront stockées. 
   ```bash
   docker volume create sqlite-data
   ```

2. **Exécution du Conteneur avec le Volume Monté** : Lancez votre conteneur en montant le volume créé à l'emplacement où votre application s'attend à trouver la base de données SQLite.
   ```bash
   docker run -d -v sqlite-data:/app/data my-web-app
   ```
   - Dans cet exemple, `my-web-app` est l'image de votre application web qui utilise SQLite.
   - `/app/data` est le dossier dans votre conteneur où l'application stocke les fichiers de base de données SQLite. Le volume `sqlite-data` est monté à cet emplacement, ce qui rend les données persistantes.

**Ce qu'il se passe** : Avec cette configuration, toutes les données générées par votre application et stockées dans la base de données SQLite sont écrites dans le volume `sqlite-data`. Même si le conteneur est arrêté, supprimé, ou redéployé, les données restent accessibles et intactes dans le volume.


##### Exemple Pratique avec PostgreSQL

**Scenario** : Vous configurez un serveur PostgreSQL dans un conteneur Docker et souhaitez garantir que les données restent persistantes pour une application qui nécessite une base de données robuste.

1. **Création d'un Volume pour PostgreSQL** : Tout comme avec SQLite, créez un volume pour stocker les données de PostgreSQL.
   ```bash
   docker volume create pgdata
   ```

2. **Lancement de PostgreSQL avec un Volume Monté** : Démarrez le conteneur PostgreSQL en montant le volume `pgdata` sur le répertoire de stockage de données de PostgreSQL.
   ```bash
   docker run -d --env-file pg_credentials.env -v pgdata:/var/lib/postgresql/data postgres
   ```
    - `docker run` : C'est la commande pour créer et démarrer un nouveau conteneur Docker.
    - `-d` : Cette option signifie "détaché" et indique à Docker d'exécuter le conteneur en arrière-plan. Cela permet à l'utilisateur de continuer à utiliser le terminal pour d'autres commandes pendant que le conteneur s'exécute.
    - `--env-file` : Cette option permet de spécifier un fichier contenant des variables d'environnement. Dans le cas de PostgreSQL, le fichier contiendrait les variables `POSTGRES_USER` et `POSTGRES_PASSWORD`. Sans variable d'environnement le container se refermera directement.
    - `-v pgdata:/var/lib/postgresql/data` : Cette option spécifie un montage de volume. Elle indique à Docker de monter le volume nommé `pgdata` dans le système de fichiers du conteneur à l'emplacement `/var/lib/postgresql/data`. C'est le répertoire où PostgreSQL stocke ses données, permettant ainsi la persistance des données de la base de données entre les redémarrages ou mises à jour du conteneur.
   - `postgres` est l'image Docker officielle de PostgreSQL.
   - `/var/lib/postgresql/data` est l'emplacement par défaut où PostgreSQL stocke ses données dans le conteneur. En montant le volume `pgdata` à cet emplacement, vous assurez la persistance des données.

**Ce qu'il se passe** : Peu importe les opérations effectuées dans la base de données, les modifications seront sauvegardées dans le volume `pgdata`. Cela signifie que vous pouvez mettre à jour, redémarrer, ou même supprimer et recréer votre conteneur PostgreSQL sans perdre de données.


En résumé, cette commande lance un conteneur PostgreSQL en arrière-plan, utilise un volume pour la persistance des données de la base de données, et se base sur l'image officielle PostgreSQL de Docker Hub.

### Avantages de l'Utilisation des Volumes pour les Bases de Données

- **Persistance des Données** : Les volumes garantissent que les données restent sauvegardées en dehors du conteneur, préservant vos données lors des mises à jour ou suppressions de conteneurs.
- **Performance** : Les volumes peuvent offrir un accès plus rapide aux données comparé aux couches d'écriture du conteneur.
- **Sécurité** : La gestion et la sauvegarde indépendantes des volumes apportent une couche supplémentaire de sécurité pour les données sensibles.

Cette section démontre comment monter un volume dans un conteneur Docker pour assurer la persistance des données, offrant ainsi un guide pratique sur l'importance des volumes dans la gestion des données avec Docker.


Nous pourrions enrichir cette section en ajoutant des informations sur les bonnes pratiques de gestion des volumes, notamment en ce qui concerne la sécurité et l'optimisation de l'espace disque. Il serait également pertinent d'expliquer comment nettoyer les volumes orphelins qui ne sont plus utilisés par aucun conteneur, car cela peut libérer de l'espace disque précieux sur l'hôte. Voici comment cette addition pourrait être structurée en markdown :


### 5.2.3 Vérifier la Taille d'un Volume Docker

Bien que Docker ne fournisse pas directement une commande pour vérifier la taille d'un volume individuel, vous pouvez utiliser les commandes système pour inspecter l'espace utilisé par un volume. Voici comment faire :

1. **Trouver le Chemin du Volume sur l'Hôte** :
   Utilisez la commande suivante pour inspecter les détails d'un volume et trouver son chemin sur le système hôte :
   ```bash
   docker volume inspect [NOM_VOLUME]
   ```
   Recherchez la valeur `Mountpoint` dans la sortie de cette commande, qui indique où les données du volume sont stockées sur l'hôte.

2. **Vérifier la Taille du Volume** :
   Une fois que vous avez le chemin du volume sur l'hôte, utilisez une commande système pour vérifier sa taille. Sous Linux, la commande `du` (Disk Usage) peut être utilisée pour cette tâche :
   ```bash
   du -sh [CHEMIN_DU_VOLUME]
   ```
   Cette commande affichera la taille totale du répertoire du volume, vous donnant une idée de l'espace disque qu'il utilise.

    Lorsque vous utilisez la commande `du` sous Linux pour vérifier la taille d'un dossier ou d'un volume, l'option `-sh` est très utile pour simplifier l'affichage des informations. Voici ce que signifient ces options :

    - **`-s`** : L'option `s` signifie "summary" (résumé). Au lieu d'afficher la taille de chaque fichier individuel dans le répertoire ciblé, `du` affichera uniquement la taille totale du répertoire. Cela est utile lorsque vous êtes uniquement intéressé par la taille globale d'un volume Docker, plutôt que par la taille de chaque fichier qu'il contient.

    - **`-h`** : L'option `h` signifie "human-readable" (lisible par l'humain). Elle ajuste l'affichage de la taille des fichiers pour la rendre plus facile à lire. Sans cette option, `du` affiche la taille en nombre de blocs d'allocation de 1 Ko (ou une unité de mesure par défaut définie par le système). Avec l'option `-h`, `du` convertit automatiquement l'affichage en unités plus grandes (Ko, Mo, Go) selon la taille du répertoire, en ajoutant l'unité appropriée à côté du chiffre pour une meilleure compréhension.

    Donc, la commande `du -sh [CHEMIN_DU_VOLUME]` est utilisée pour obtenir un résumé de l'espace disque utilisé par le volume Docker, affiché de manière à ce que la taille soit facile à comprendre, par exemple, "250M" pour 250 mégaoctets ou "2G" pour 2 gigaoctets. Cela simplifie grandement la gestion de l'espace disque et la planification de la capacité pour les utilisateurs de Docker.

Ces étapes vous permettent de surveiller l'utilisation de l'espace disque par les volumes Docker, ce qui est particulièrement important dans les environnements de production où la gestion efficace de l'espace disque est essentielle.


## 5.2.4 Bonnes Pratiques et Nettoyage des Volumes

Après avoir abordé la création, l'utilisation et la persistance des données avec les volumes Docker, il est important de considérer certaines bonnes pratiques pour maintenir l'efficacité et la sécurité de votre environnement Docker.

### Bonnes Pratiques pour Gérer les Volumes

- **Sécurité des Données** : Assurez-vous que les données sensibles stockées dans les volumes sont correctement sécurisées, en utilisant par exemple des mécanismes de chiffrement si nécessaire.
- **Gestion de l'Espace Disque** : Les volumes peuvent rapidement utiliser un espace disque conséquent. Il est donc crucial de surveiller régulièrement l'espace utilisé et de supprimer les volumes qui ne sont plus nécessaires.

### Nettoyage des Volumes Orphelins

Les volumes non associés à un conteneur actif sont considérés comme orphelins. Bien qu'ils puissent contenir des données importantes, dans de nombreux cas, ils résultent de conteneurs supprimés et peuvent être nettoyés pour libérer de l'espace.

**Trouver et supprimer les volumes orphelins** :
   ```bash
   docker volume prune
   ```
Cette commande supprime tous les volumes non utilisés par au moins un conteneur. Docker vous demandera de confirmer la suppression. C'est un moyen efficace de récupérer de l'espace disque, mais assurez-vous de vérifier que les données stockées dans ces volumes ne sont plus nécessaires.

En suivant ces bonnes pratiques et en nettoyant régulièrement votre système, vous pouvez maintenir un environnement Docker propre, sécurisé, et optimisé en termes d'utilisation des ressources.
