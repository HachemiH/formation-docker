# 5.3 Les Bind Mounts

Les bind mounts sont particulièrement utiles en développement, offrant une manière de refléter immédiatement les modifications du code dans le conteneur sans nécessiter de reconstruire l'image Docker. Cette méthode s'avère essentielle pour les workflows de développement rapide.

## 5.3.1 Pourquoi utiliser les Bind Mounts ?

- **Développement et Test** : Permettent une itération rapide en reflétant directement les modifications du code local dans le conteneur.
- **Accès Direct aux Données de l'Hôte** : Facilitent l'accès aux fichiers ou dossiers spécifiques de l'hôte depuis le conteneur.
- **Persistance de Données** : Offrent une solution pour la persistance des données nécessitant un contrôle précis sur les chemins de fichiers.

## 5.3.2 Création et Utilisation

### 5.3.2.1 Commandes Détaillées

Les bind mounts dans Docker peuvent être spécifiés de deux manières lors du lancement d'un conteneur : via `-v` ou `--mount`.

#### 5.3.2.1.1 Utilisation de `-v` ou `--volume`

```bash
docker run -d -v /chemin/sur/hote:/chemin/dans/conteneur mon_image
```
- **`-d`** : Exécute le conteneur en arrière-plan.
- **`-v`** : Crée un bind mount entre un chemin sur l'hôte et un chemin dans le conteneur.
   - `/chemin/sur/hote` : Chemin absolu sur l'hôte.
   - `/chemin/dans/conteneur` : Chemin cible dans le conteneur.

#### 5.3.2.1.2 Utilisation de `--mount`

```bash
docker run -d --mount type=bind,source=/chemin/sur/hote,target=/chemin/dans/conteneur mon_image
```
- **`--mount`** : Offre une syntaxe plus détaillée pour le montage.
   - `type=bind` : Spécifie le montage en tant que bind mount.
   - `source=/chemin/sur/hote` : Indique le chemin sur l'hôte.
   - `target=/chemin/dans/conteneur` : Définit le chemin cible dans le conteneur.

### 5.3.2.2 Bonnes Pratiques

- **Sécurité** : Prenez garde aux implications de sécurité, car les bind mounts permettent un accès direct aux systèmes de fichiers de l'hôte.
- **Gestion des Chemins** : Veillez à une gestion précise des chemins pour prévenir les conflits ou les accès indésirables.
- **Combinaison avec les Volumes** : Utilisez les bind mounts pour des besoins spécifiques de développement et préférez les volumes Docker pour la persistance des données à long terme.

