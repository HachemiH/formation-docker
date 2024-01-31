# 4.3. Introduction au Dockerfile

Le Dockerfile est un élément central de l'écosystème Docker, surtout quand il s'agit de créer des images personnaliséess. Imaginez-le comme le plan d'architecte pour votre image Docker : chaque instruction représente une étape précise dans le processus de construction, assurant que l'image finale soit exactement conforme à vos exigences.

## 4.3.1 Qu'est-ce qu'un Dockerfile ?

Un Dockerfile est un fichier texte qui contient une série d'instructions permettant de construire automatiquement une image Docker. C'est comme une recette de cuisine pour votre application : il détaille les ingrédients (dépendances, environnements, fichiers, etc.) et les étapes (commandes) pour préparer votre "plat" (l'image Docker).

## 4.3.2 Comprendre la Structure d'un Dockerfile

### 4.3.2.1 Structure et Syntaxe de Base

La structure d'un Dockerfile est simple et directe. Chaque ligne dans un Dockerfile représente une instruction, et chaque instruction crée une nouvelle couche dans l'image Docker. Ces instructions peuvent inclure :

- `FROM`: pour définir l'image de base. C'est comme choisir le système d'exploitation ou l'environnement de base pour votre application.
- `RUN`: pour exécuter des commandes dans le shell. Cela peut être utilisé pour installer des logiciels ou configurer des paramètres.
- `COPY` et `ADD`: pour copier des fichiers et des répertoires de votre ordinateur vers l'image Docker.
- `CMD` et `ENTRYPOINT`: pour définir la commande par défaut à exécuter lors du démarrage du conteneur.
- `EXPOSE`: pour indiquer les ports sur lesquels le conteneur sera à l'écoute.

### 4.3.2.2 Instructions Courantes dans un Dockerfile

Voici quelques instructions couramment utilisées dans un Dockerfile :

- `WORKDIR`: Définit le répertoire de travail pour les instructions `RUN`, `CMD`, `ENTRYPOINT`, `COPY` et `ADD`.
- `ENV`: Permet de définir des variables d'environnement.
- `VOLUME`: Crée un point de montage pour accéder et stocker des données persistantes.
- `USER`: Définit l'utilisateur qui exécutera les conteneurs créés à partir de l'image.


### 4.3.2.3 Format dans un Dockerfile

- **Format de Fichier**: Le Dockerfile est un fichier texte sans extension spécifique. Son nom est toujours `Dockerfile` (avec un "D" majuscule).
- **Instructions**: Chaque ligne d'un Dockerfile commence par une instruction. Ces instructions indiquent à Docker comment construire l'image.
- **Commentaires**: Les commentaires commencent par `#`. Ils sont ignorés par Docker mais sont utiles pour la documentation.


### 4.3.2.4 Structure Habituelle d'un Dockerfile de Base

Un Dockerfile de base suit généralement cette structure :

1. Définir l'image de base avec `FROM`.
2. Définir le répertoire de travail avec `WORKDIR`.
3. Copier les fichiers nécessaires dans le conteneur avec `COPY` ou `ADD`.
4. Installer des dépendances ou exécuter des scripts de configuration avec `RUN`.
5. Définir les ports à exposer avec `EXPOSE` (si nécessaire).
6. Définir la commande par défaut avec `CMD`.

