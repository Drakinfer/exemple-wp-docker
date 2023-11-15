# Containerisation de l'Application WordPress
Ce projet présente une version containerisée de l'application WordPress. Le code source est accessible à l'URL suivante : lien vers le dépôt GitHub.

## Configuration des Services
La mise en place de cette application nécessite l'orchestration de quatre services via un fichier docker-compose.yml :

Un service MariaDB 10.3 pour la gestion de la base de données.
Un service Adminer pour faciliter la connexion à la base de données.
Un service utilisant notre Dockerfile personnalisé.
Un service pour exécuter Nginx.

## Installation du Projet
Suivez ces étapes pour déployer l'application sur votre machine locale :

Clonez le dépôt vers votre machine.
```bash
git clone https://github.com/tasmer/exemple-wp-docker
```

Utilisez la commande suivante pour construire et démarrer les conteneurs.
```bash
`docker-compose up --build
```

Installez les dépendances du projet avec Composer.
```bash
`docker-compose exec wp composer install
```

Copiez le fichier .env.example vers un nouveau fichier .env et configurez les accès à la base de données.
```bash
`docker-compose exec wp cp .env.example .env`
```

Éditez le fichier .env avec les informations de la base de données :
.env
```bash
DB_NAME=wp
DB_USER=root
DB_PASSWORD=R00t
DB_HOST=mariadb
WP_HOME=http://localhost
```
Accédez à http://localhost dans votre navigateur pour visualiser l'application WordPress.

## Commandes Utiles
```bash
docker-compose up --build : Construit et démarre les conteneurs.
```
```bash
docker-compose down : Arrête et supprime les conteneurs.
```
```bash
docker-compose exec wp composer install : Installe les dépendances du projet avec Composer.
```
Note : Si vous souhaitez installer la ligne de commande WordPress (WP-CLI), suivez les instructions fournies ici et ajustez le Dockerfile en conséquence. Cette étape est facultative mais peut vous apporter des fonctionnalités supplémentaires.