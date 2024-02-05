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


### 4.3.2.5 Exemple basique de Dockerfile

```Dockerfile
# Utilise l'image officielle Nginx comme image de base
FROM nginx:alpine

# Définit le répertoire de travail dans le conteneur
WORKDIR /usr/share/nginx/html

# Copie les fichiers de l'application web statique depuis le répertoire actuel vers le répertoire de travail dans le conteneur
COPY . .

# Expose le port 80
EXPOSE 80

# Utilise la commande par défaut de l'image Nginx pour démarrer le serveur
CMD ["nginx", "-g", "daemon off;"]
```

Explications :

- **`FROM nginx:alpine`** : Cette ligne indique que l'image sera construite à partir de l'image officielle Nginx utilisant la version "alpine", qui est une version légère d'Alpine Linux. Cela sert de point de départ et fournit Nginx prêt à l'emploi.

- **`WORKDIR /usr/share/nginx/html`** : Cette commande définit le répertoire de travail dans le conteneur. C'est là que les fichiers de notre site seront servis par Nginx.

- **`COPY . .`** : L'instruction `COPY` est utilisée pour copier des fichiers et des dossiers de votre machine locale dans l'image Docker que vous êtes en train de construire. Cette commande prend deux arguments principaux : le premier spécifie le chemin source (où les fichiers se trouvent sur votre machine) et le second spécifie le chemin de destination (où les fichiers seront placés dans l'image Docker).

    Dans cet exemple `COPY . .`, les deux points sont utilisés pour indiquer :
    - Le premier `.` (point) représente le répertoire dans lequel se trouve le Dockerfile sur votre machine locale. Cela signifie "prendre tous les fichiers et dossiers présents dans ce répertoire".
    - Le deuxième `.` (point) se réfère au répertoire de travail actuel à l'intérieur de l'image Docker, qui a été défini préalablement par l'instruction `WORKDIR`. Si, par exemple, `WORKDIR /usr/share/nginx/html` a été spécifié, alors le deuxième `.` représente ce chemin dans l'image Docker.

    Ainsi, `COPY . .` signifie "copier tous les fichiers et dossiers du répertoire courant (où se trouve le Dockerfile sur la machine locale) dans le répertoire de travail actuel à l'intérieur de l'image Docker".

    C'est une manière concise de transférer le contenu de votre application (comme les fichiers HTML, CSS, JavaScript pour un site web) de votre environnement de développement vers l'environnement de l'image Docker, permettant à cette dernière d'accéder aux fichiers nécessaires pour exécuter l'application.

- **`EXPOSE 80`** : Indique que le conteneur écoute sur le port 80. C'est le port par défaut pour le trafic web HTTP.

- **`CMD ["nginx", "-g", "daemon off;"]`** : Définit la commande par défaut pour le conteneur, qui dans ce cas, démarre le serveur Nginx en mode foreground (pas en tant que daemon). Cela permet au conteneur de rester actif et de servir le site web.

