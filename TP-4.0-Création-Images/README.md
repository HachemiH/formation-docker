# TP du Module sur la Création d'image Docker

Ce TP est à réaliser à l'aide de votre terminal, en local.

<a href='https://github.com/Simplon-hdf/Docker-TP-4.0--Nest-API'>Lien vers l'API Nest à conteneuriser</a>
Cette API utilise le port 3000 et nécessite un environnement `node` afin de s'exécuter.

## Conteneurisation d'une API Nest Basique

1. Récupérer le code de l'API sur votre machine.
2. Écrire le `DockerFile` permettant de créer une image de cette API à la racine de l'application.
   1. L'image de base est `node:hydrogen-slim`.
   2. Le DockerFile doit contenir une commande `npm i`.
   3. Le DockerFile doit contenir une commande d'exécution de l'API (`npm run start`).
   4. Le DockerFile doit exposé le port de l'application.
3. Créer un fichier `.dockerignore` pour alléger l'image de l'API, ce fichier doit lister les fichiers non essentiels au bon fonctionnement de l'API.