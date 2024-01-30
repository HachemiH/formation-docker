# 2.3 Comment installer Docker sur Linux

## Étapes d'installation

1. **Vérification de la compatibilité** :
   - Assurez-vous que votre système est compatible avec Docker Desktop.

2. **Téléchargement du paquet d'installation** :
   - Rendez-vous sur le [site officiel de Docker](https://www.docker.com/).
   - Téléchargez le paquet adapté à votre distribution (`.deb` pour Debian/Ubuntu, `.rpm` pour Fedora/Red Hat).

3. **Installation de Docker** :
   - Ouvrez un terminal.
   - Pour Debian/Ubuntu, utilisez : `sudo dpkg -i chemin_vers_le_paquet.deb`.
   - Pour Fedora/Red Hat, utilisez : `sudo dnf install chemin_vers_le_paquet.rpm`.

4. **Démarrage de Docker** :
   - Lancez Docker Desktop via votre interface graphique ou avec la commande `docker-desktop` dans le terminal.

5. **Vérification de l'installation** :
   - Confirmez l'installation en tapant `docker --version` dans le terminal.
