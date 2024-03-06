# 2. Écrire le ``DockerFile`` permettant de créer une image de cette API à la racine de l'application

Voici le Dockerfile associé à l'application :

```Dockerfile
FROM node:hydrogen-slim

WORKDIR /api/
COPY . .
RUN npm i
EXPOSE 3000

CMD ["/bin/bash", "-c", "npm run start"]
```

- `FROM` : Définit l'image de base, ici `node:hydrogen-slim`.
- `WORKDIR` : Définit le répertoire de travail.
- `COPY` : Copie les fichiers de l'image de l'hôte depuis le chemin vers le chemin dans les conteneurs qui démarreront de l'image.
  - `.` : Le dossier dans lequel se trouve le `DockerFile`.
  - ` .` : Le chemin d'accès `/api/`.
- `RUN npm i` : Exécute la commande `npm install`
- `EXPOSE 3000` : Expose le port `3000` (celui de NestJS par défaut) pour permettre la communication avec l'application qui sera conteneurisé.
- `CMD ...` : Exécute une commande avec le shell `bash` de l'image de base
  - `"/bin/bash"` : Représente le shell à utiliser.
  - `"-c"` : Oblige l'utilisation de `bash` au lieu de `sh`. 
  - `npm run start` : Éxecute la commande de démarrage de l'application
