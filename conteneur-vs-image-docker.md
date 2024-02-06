# 3.1. Quelle est la différence entre un conteneur Docker et une image Docker ?

Pour bien comprendre cette différence, introduisons d'abord le concept d'**instance**.

## Instance :
Imaginez une chanson sur une plateforme de streaming comme Spotify. Chaque fois que vous jouez cette chanson, vous créez une "instance" de cette chanson. Même si la chanson originale est la même pour tout le monde, chaque écoute est une instance unique pour l'auditeur.

## Image Docker :
Une image Docker est comparable à la chanson enregistrée sur Spotify. C'est une sorte de "blueprint" ou de recette qui contient toutes les instructions et les fichiers nécessaires pour créer un conteneur Docker. L'image est immuable, c'est-à-dire qu'elle ne change pas, mais elle peut être transférée (téléchargée ou partagée), modifiée (par création d'une nouvelle image), ou supprimée selon les besoins.

## Conteneur Docker :
Un conteneur Docker, en revanche, est comme la chanson que vous jouez actuellement sur votre appareil. C'est une instance en temps réel de l'image Docker. Chaque conteneur est une application ou un environnement isolé et exécutable qui fonctionne à partir de l'image mais dans son propre espace indépendant.

En résumé, l'image Docker est le modèle original (comme la chanson sur Spotify) et le conteneur Docker est une instance exécutable de ce modèle (comme la chanson jouée sur votre appareil).
