## 3.5 Comment exécuter des commandes à l'intérieur d'un conteneur Docker ?

L'une des fonctionnalités les plus puissantes de Docker est la capacité d'interagir avec les conteneurs en cours d'exécution. Cela permet aux développeurs et aux administrateurs système de gérer et de dépanner les applications contenues de manière plus efficace.

### 3.5.1. Accéder au shell d'un conteneur Docker

La commande `docker exec` est essentielle pour exécuter des processus à l'intérieur d'un conteneur actif. Elle est souvent utilisée pour accéder au shell du conteneur, vous permettant d'exécuter des commandes comme si vous étiez dans un terminal Linux standard.

Exemple :
```bash
docker exec -it [CONTENEUR_ID_OU_NOM] bash
```

Ici, `-it` permet une interaction interactive (le `i` pour interactif et le `t` pour terminal). Cela ouvre une session dans le shell du conteneur, où vous pouvez exécuter n'importe quelle commande Linux.

### 3.5.2. Exécuter une commande spécifique dans un conteneur

Si vous devez exécuter une commande unique sans rester dans le shell, vous pouvez le faire directement avec `docker exec`.

Exemple :
```bash
docker exec [CONTENEUR_ID_OU_NOM] [COMMANDE]
```

Cette commande exécute `[COMMANDE]` dans le conteneur spécifié et se termine immédiatement après.

### 3.5.3. Interagir avec des processus en cours d'exécution

Cette capacité à interagir avec les conteneurs offre une flexibilité considérable pour la gestion des applications. Vous pouvez dépanner des problèmes, ajuster des configurations ou simplement explorer l'état actuel du conteneur.

---

Ces techniques d'interaction avec les conteneurs sont fondamentales dans la gestion quotidienne des environnements Docker. Elles permettent une maintenance et un dépannage efficaces, essentiels pour garantir la santé et la performance des applications en conteneurs.

