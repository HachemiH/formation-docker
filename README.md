# Formation Docker

#### Module 1.0: Introduction à Docker
- **1.1. Découverte de Docker**
- **1.2. Avantages et Usages de Docker**

#### Module 2.0: Installation de Docker
- **2.1. Installer Docker sur Windows**
- **2.2. Installer Docker sur MacOS**
- **2.3. Installer Docker sur Linux**

#### Module 3.0: Comprendre les Conteneurs et les Images Docker
- **3.1. Introduction aux Conteneurs et aux Images**
- **3.2. Gérer les Images Docker**
  - Commandes : `docker images`, `docker pull [IMAGE]`, `docker rmi [IMAGE]`
- **3.3. Exécution et Exploration de Conteneurs**
  - Commandes : `docker run [IMAGE]`, `docker ps`, `docker inspect [CONTENEUR]`
- **3.4. Interaction avec les Conteneurs**
  - Commandes : `docker exec -it [CONTENEUR] bash`
- **3.5. Cycle de Vie d'un Conteneur**
  - Commandes : `docker stop [CONTENEUR]`, `docker start [CONTENEUR]`, `docker rm [CONTENEUR]`
- **3.6. Nettoyage et Gestion des Ressources**
  - Commandes : `docker container prune`, `docker image prune`

#### Module 4.0: Images Docker
- **4.1. Travailler avec les Images Docker**
- **4.2. Création d'Images Personnalisées**
  - Commandes : `docker build -t nom_image .`

#### Module 5.0: Stockage avec Docker
- **5.1. Gestion des Données avec Volumes**
  - Commandes : `docker volume create`, `docker volume inspect`
- **5.2. Utilisation Pratique des Volumes**
  - Commandes : `docker run -v nom_volume:/chemin_conteneur`

#### Module 6.0: Réseaux avec Docker
- **6.1. Fondamentaux des Réseaux Docker**
  - Commandes : `docker network ls`, `docker network create`
- **6.2. Configuration des Réseaux pour les Conteneurs**
  - Commandes : `docker run --network=nom_reseau`

#### Module 7.0: Docker Compose et Applications Multi-Conteneurs
- **7.1. Introduction à Docker Compose**
  - Commandes : `docker-compose up`, `docker-compose down`
- **7.2. Gestion d'Applications avec Docker Compose**
  - Commandes : Écriture de `docker-compose.yml`

