# 1.3 Pourquoi utiliser Docker ? Quels problèmes résout-il et quels sont ses avantages ?


## 1.3.1 Problèmes Résolus par Docker
1. **Incohérences entre Environnements :** Assure une cohérence entre les environnements de développement, de test et de production.
   - Exemple : Une application qui fonctionne sur l'ordinateur d'un développeur mais rencontre des erreurs sur un autre système. Docker garantit la même configuration partout, éliminant le classique "ça marche sur ma machine".

2. **Conflits de Dépendances :** Isolation des applications avec leurs propres dépendances pour éviter les conflits.
   - Exemple : Deux applications nécessitant différentes versions de Python. Docker permet d'isoler chaque application avec sa propre version de Python, évitant tout conflit.

3. **Complexité de Déploiement :** Simplification du déploiement d'applications complexes.
   - Exemple : Déploiement d'une application web complexe avec base de données, serveur web, et autres services. Docker permet de "containeriser" chaque service pour simplifier le déploiement et la maintenance.

## 1.3.2 Avantages de Docker
1. **Portabilité :** Fonctionne sur toute machine avec Docker, indépendamment du système d'exploitation.
   - Exemple : Une application Dockerisée peut être exécutée aussi bien sur un ordinateur Windows, un Mac ou un serveur Linux sans aucune modification.

2. **Isolation :** Sécurité accrue et réduction des interférences entre applications.
   - Exemple : Plusieurs applications s'exécutant sur le même serveur sans interférer entre elles, chacune opérant dans son propre "sandbox" Docker.

3. **Efficacité des Ressources :** Moins gourmand que les machines virtuelles traditionnelles.
   - Exemple : Exécuter plusieurs conteneurs sur un seul serveur physique ou virtuel, chaque conteneur utilisant seulement les ressources nécessaires, contrairement aux machines virtuelles qui nécessitent des ressources dédiées pour chaque instance.

4. **Facilité de Gestion :** Outils et commandes intuitifs pour la gestion des conteneurs et des images.
   - Exemple : Utilisation de commandes simples comme `docker run` pour démarrer une application ou `docker ps` pour voir quelles applications s'exécutent.

5. **Intégration et Déploiement Continus (CI/CD) :** Facilite la mise en place de pipelines CI/CD pour des mises à jour fréquentes et fiables.
   - Exemple : Mise à jour automatique d'une application web en production dès qu'un changement est apporté dans le code source, grâce à l'intégration de Docker dans les pipelines CI/CD.

