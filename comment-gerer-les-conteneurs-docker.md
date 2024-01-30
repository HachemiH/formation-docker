## 3.4. Comment gérer les conteneurs Docker ?

Les conteneurs Docker sont des instances exécutables de vos images Docker. Ils sont comme des versions allégées et plus flexibles des machines virtuelles. Comprendre la gestion des conteneurs est essentiel pour utiliser Docker efficacement.

### 3.4.1. Comment démarrer un conteneur Docker ?

Pour démarrer un conteneur à partir d'une image, utilisez la commande `docker run`. Par exemple, pour lancer un conteneur avec l'image `hello-world` :

```bash
docker run hello-world
```

Cette commande crée et lance une nouvelle instance de conteneur à partir de l'image spécifiée.

### 3.4.2. Comment lister les conteneurs actifs ?

La commande `docker ps` (ps pour "process status") vous permet de voir les conteneurs actuellement en cours d'exécution :

```bash
docker ps
```

Elle affiche une liste des conteneurs actifs avec des détails comme l'ID du conteneur, l'image utilisée, et l'état du conteneur.

### 3.4.3. Comment stopper un conteneur Docker ?

Pour arrêter un conteneur en cours d'exécution, utilisez `docker stop` suivi de l'ID ou du nom du conteneur :

```bash
docker stop [CONTENEUR_ID_OU_NOM]
```

Cela arrêtera le conteneur spécifié.

### 3.4.4. Comment supprimer un conteneur Docker ?

Une fois un conteneur arrêté, vous pouvez le supprimer avec la commande `docker rm` (rm pour "remove") :

```bash
docker rm [CONTENEUR_ID_OU_NOM]
```

Cette commande supprime le conteneur de votre système, libérant ainsi de l'espace.

---

Ces commandes de base vous donnent un bon contrôle sur vos conteneurs Docker. Dans les prochaines sections, nous explorerons des fonctionnalités plus avancées comme l'exécution de commandes à l'intérieur d'un conteneur et la surveillance de leur état.

