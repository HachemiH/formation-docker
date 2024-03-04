# 2. Créer un fichier ``docker-compose.yml`` dans le dossier ``back-end``.

```yaml
version: '3'
services:
  db:
    image: postgres:12.2
    container_name: my-database
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: deom
      POSTGRES_PASSWORD: test
    volumes:
      - pgdata:/var/lib/postgresql/data
    networks:
      - back-network

  nginx:
    image: nginx:latest
    container_name: my-nginx
    ports:
      - "80:80"
    networks:
      - back-network

volumes:
  pgdata:
    name: pgdata
networks:
  back-network:
    name: back-network
    driver: bridge
```

- `services`: Définit les différents services à exécuter (Il est possible de nommer les services comme vous le voulez).
  - `image`: Définit l'image du service (du conteneur).
  - `container_name`: Définit un nom pour les conteneurs crées par le Docker Compose.
  - `port`: Définit les ports du conteneur.
  - `environment`: Permet de définir les variables d'environnement du conteneur.
  - `volumes`: Permet de définir le volume (ou le bind-mount) utilisé par le conteneur.
  - `networks`: Permet de définir le réseaux auquel le conteneur sera connecté.

```yaml
volumes:
  pgdata:
    name: pgdata
networks:
  back-network:
    name: back-network
    driver: bridge
```

- `volumes`: Permet de créer un ou plusieurs volumes.
- `networks`: Permet de créer un ou plusieurs réseaux. 