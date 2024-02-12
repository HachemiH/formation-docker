# 4.4 Construction d'une Image Docker Personnalisée

Dans cette section, nous allons prendre comme exemple le Dockerfile de base pour Nginx présenté précédemment et vous montrer comment personnaliser l'image en modifiant le fichier `index.html` de Nginx. Cela vous permettra de déployer votre propre contenu web statique via un conteneur Docker.

## Étape 1: Préparer votre Environnement de Travail

1. Créez un répertoire sur votre machine locale pour votre projet Docker. Vous pouvez le nommer `mon-site-web`.
2. À l'intérieur de ce répertoire, créez un fichier `Dockerfile` sans extension.
3. Créez également un répertoire `site-web` où vous placerez le contenu de votre site, par exemple un fichier `index.html` personnalisé.

## Étape 2: Modifier le Contenu Web

Dans le répertoire `site-web`, créez ou modifiez le fichier `index.html` pour personnaliser le contenu de votre site web. Voici un exemple simple :

```html
<!DOCTYPE html>
<html>
<head>
    <title>Mon Site Dockerisé</title>
</head>
<body>
    <h1>Bienvenue sur mon site web Dockerisé!</h1>
    <p>Ce site est servi depuis un conteneur Docker utilisant Nginx.</p>
</body>
</html>
```

## Étape 3: Mettre à Jour le Dockerfile

Ouvrez votre `Dockerfile` et assurez-vous qu'il ressemble à ceci :

```Dockerfile
# Utilise l'image officielle Nginx comme image de base
FROM nginx:alpine

# Définit le répertoire de travail dans le conteneur
WORKDIR /usr/share/nginx/html

# Copie le contenu du site web dans le conteneur
COPY site-web/ .

# Expose le port 80
EXPOSE 80

# Utilise la commande par défaut de l'image Nginx pour démarrer le serveur
CMD ["nginx", "-g", "daemon off;"]
```

Notez que nous avons modifié l'instruction `COPY` pour copier le contenu du répertoire `site-web/` de votre machine locale vers le répertoire de travail dans le conteneur.

## Étape 4: Construire l'Image Docker

Dans le répertoire contenant votre `Dockerfile`, exécutez la commande suivante pour construire votre image Docker personnalisée :

```bash
docker build -t mon-site-web:latest .
```

Cette commande construit une image Docker à partir de votre Dockerfile, en taguant l'image avec le nom `mon-site-web` et le tag `latest`.

## Étape 5: Exécuter votre Conteneur Docker

Une fois l'image construite, vous pouvez démarrer un conteneur en utilisant votre image personnalisée :

```bash
docker run --name mon-site-web -d -p 8080:80 mon-site-web:latest
```

Cette commande démarre un conteneur nommé `mon-site-web` en utilisant l'image que vous avez construite, mappant le port 8080 de votre machine hôte sur le port 80 du conteneur.

## Conclusion

Vous avez maintenant une image Docker personnalisée qui sert votre propre contenu web statique via Nginx. En accédant à `http://localhost:8080` sur votre navigateur, vous devriez voir votre page web personnalisée servie par Nginx à partir de votre conteneur Docker. 

Cet exemple illustre comment vous pouvez personnaliser les images Docker pour répondre à vos besoins spécifiques, en vous permettant de déployer des applications et des services de manière flexible et isolée.

