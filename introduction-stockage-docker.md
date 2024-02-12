# 5.1 Introduction au Stockage dans Docker

Imaginez jouer à un jeu vidéo sur votre console, progressant à travers les niveaux, recueillant des objets et des succès. Si la console ne sauvegarde pas votre progression, vous devrez recommencer depuis le début chaque fois que vous l'éteignez. C'est un peu ce qui arrive avec les conteneurs Docker sans un mécanisme de stockage persistant : sans celui-ci, toutes les modifications et les données générées dans le conteneur sont perdues lorsque celui-ci est supprimé ou redémarré. Docker propose plusieurs solutions pour sauvegarder et gérer ces données, assurant ainsi qu'elles persistent au-delà du cycle de vie des conteneurs.

## 5.1.1 Les Mécanismes de Stockage dans Docker

- **Volumes :** Les volumes sont comme des disques durs externes pour vos conteneurs, gérés par Docker et stockés hors du système de fichiers du conteneur. Ils permettent de conserver et de partager des données entre conteneurs et avec l'hôte, assurant leur persistance même après la suppression des conteneurs.

- **Bind Mounts :** Pensez aux bind mounts comme à des clés USB que vous pouvez connecter à différents ordinateurs. Ils permettent de monter un dossier ou un fichier existant sur l'hôte directement dans un conteneur, offrant une manière pratique de travailler sur les fichiers de l'hôte depuis le conteneur.

- **Tmpfs Mounts :** Les tmpfs mounts sont comparables à des notes autocollantes que vous utilisez pour des rappels temporaires. Ils stockent des données en mémoire RAM, sans persistance sur le disque dur, idéal pour les informations temporaires ou sensibles qui ne doivent pas être conservées après l'arrêt du conteneur.

Utiliser ces solutions de stockage permet de gérer efficacement les données dans vos projets Docker, en choisissant la bonne méthode selon les besoins de persistance, de performance et de sécurité.
