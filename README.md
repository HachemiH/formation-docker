# Formation Docker

## Module 1.0: Introduction à Docker
- **1.1. Qu'est-ce que Docker?**
- **1.2. Pourquoi Utiliser Docker? Quels sont ses Avantages?**

## Module 2.0: Installation de Docker
- **2.1. Comment Installer Docker sur Windows?**
- **2.2. Comment Installer Docker sur MacOS?**
- **2.3. Comment Installer Docker sur Linux?**

## Module 3.0: Fondamentaux des Conteneurs et des Images
- **3.1. Quelle est la Différence entre un Conteneur Docker et une Image Docker?**
- **3.2. Comment Gérer les Images Docker?**
  - `docker images`
  - `docker pull [IMAGE]`
  - `docker rmi [IMAGE]`
- **3.3. Comment Créer et Exécuter des Conteneurs Docker?**
  - `docker run [IMAGE]`
  - `docker ps`
- **3.4. Comment Interagir avec les Conteneurs Docker?**
  - `docker exec -it [CONTENEUR] bash`
- **3.5. Comment Surveiller et Dépanner un Conteneur Docker?**
  - `docker logs [CONTENEUR]`
  - `docker inspect [CONTENEUR]`

## Module 4.0: Gestion Avancée des Images
- **4.1. Comment Construire une Image Docker Personnalisée?**
  - `docker build -t [nom_image] .`
- **4.2. Comment Optimiser les Images Docker?**

## Module 5.0: Stockage dans Docker
- **5.1. Comment Utiliser les Volumes Docker?**
  - `docker volume create [nom_volume]`
  - `docker run -v [nom_volume]:[chemin_dans_conteneur]`

## Module 6.0: Réseautage dans Docker
- **6.1. Quels sont les Concepts de Base du Réseau dans Docker?**
  - `docker network ls`
  - `docker network create [nom_reseau]`
- **6.2. Comment Connecter des Conteneurs à des Réseaux Docker?**
  - `docker run --network=[nom_reseau] [IMAGE]`

## Module 7.0: Docker Compose et Orchestration
- **7.1. Qu'est-ce que Docker Compose et Comment l'Utiliser?**
  - `docker-compose up`
  - `docker-compose down`

