# TP 6 : Réseautage dans Docker

Ce TP est à réaliser sur le VPS qui vous a été fourni.

1. Créer un réseau (sur le driver local) nommé `back-end-network`.
2. Vérifier que le réseau `back-end-network` à bien été crée.
3. Consulter les informations détaillées du réseau `back-end-network`.
4. Démarrer un conteneur de l'image `nginx` en le connectant au réseau `back-end-network`.
5. Consulter les informations détaillées du réseau `back-end-network`.
   1. Quelles sont les différences ?
6. Démarrer un conteneur de l'image `postgres` en le connectant au réseau `back-end-network`.
7. Consulter les informations détaillées du conteneur `postgres`.
   1. Quelles observations pouvez-vous faire ?
8. Supprimer le réseau `back-end-network`.
   1. Si cela fonctionne, quel est le retour ?
   2. Si cela ne fonctionne pas, pourquoi ?