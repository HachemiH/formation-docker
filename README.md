# 3. Créer un fichier ``.dockerignore`` pour alléger l'image de l'API, ce fichier doit lister les fichiers non essentiels au bon fonctionnement de l'API.

Voici le `.dockerignore` associé à l'application :

```dockerignore
dist/
node_modules/
.eslintrc.js
.prettierrc
```

- `dist/` : Exclue les fichiers transpilés de l'application
- `node_modles/` : Exclue les dépendances de l'application
- `.eslintrc.js`, `.prettierrc` : Exclue les fichiers assurant la qualité du code.