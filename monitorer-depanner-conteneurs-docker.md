# 3.6. Comment surveiller et dépanner un conteneur Docker ?

La surveillance et le dépannage des conteneurs Docker sont cruciaux pour le maintien de la performance et la stabilité de vos applications. Voici les étapes et commandes essentielles pour effectuer ces tâches :

## Surveillance des Conteneurs

- **Lister les Conteneurs Actifs et Inactifs :**
  - Commande : `docker ps -a`
    - `docker ps` affiche les conteneurs actuellement en cours d'exécution.
    - Ajoutez `-a` pour voir tous les conteneurs, y compris ceux qui sont arrêtés.
  
- **Vérifier les Logs des Conteneurs :**
  - Commande : `docker logs [CONTENEUR]`
    - Permet de consulter les logs d'un conteneur spécifique, utile pour comprendre son comportement et identifier d'éventuels problèmes.

- **Analyser l'Utilisation des Ressources par les Conteneurs :**
  - Commande : `docker stats`
    - Affiche l'utilisation des ressources (CPU, mémoire, réseau) par les conteneurs en temps réel.

## Dépannage des Conteneurs

- **Inspecter un Conteneur :**
  - Commande : `docker inspect [CONTENEUR]`
    - Fournit des informations détaillés sur la configuration du conteneur, incluant la configuration réseau, les volumes montés, et d'autres métadonnées importantes.

- **Exécution de Commandes de Diagnostic à l'Intérieur d'un Conteneur :**
  - Commande : `docker exec -it [CONTENEUR] [COMMANDE]`
    - Permet d'exécuter des commandes spécifiques à l'intérieur du conteneur pour le diagnostic.

- **Redémarrer un Conteneur :**
  - Commande : `docker restart [CONTENEUR]`
    - Redémarrer un conteneur peut souvent résoudre des problèmes temporaires.

- **Supprimer et Recréer un Conteneur Défaillant :**
  - Commande : `docker rm [CONTENEUR]`
    - Si un conteneur est corrompu ou ne fonctionne plus correctement, il peut être nécessaire de le supprimer et de le recréer.
