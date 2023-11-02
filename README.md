# Containerisation de cette Application

Vous devez containeriser cette application avec un fichier `docker-compose.yml``

Nous avons besoin de 4 services :

 1. un service avec **MariaDB 10.3** pour la gestion de notre base de données
 2. Un service  avec **Adminer** pour nous connecter sur la base de données
 3. Un service qui va utiliser notre **Dockerfile**
 4. Un service pour exécuter **Nginx**.

## Informations à prendre en compte pour votre docker-compose

- Les deux derniers services (Nginx et celui qui utilise le Dockerfile) devront avoir un **Volume** qui pointe sur `/usr/share/nginx/html` pour monter le code source du projet dans ce dossier.

- Vous devez surcharger la configuration de base de PHP-FPM par la configuration fournie dans `docker/config/php-fpm.conf`. La configuration de PHP-FPM se trouve dans `/usr/local/etc/php-fpm.d/www.conf` au niveau du container. Vous pouvez soit modifier le **Dockerfile** pour copier ce fichier dans l'image, soit utiliser docker-compose pour surcharger le fichier.

- Pour la configuration de Nginx, faites une surcharge depuis le fichier **docker-compose.yml**. Le fichier suivant `docker/config/nginx.conf` doit remplacer celui du container `/etc/nginx/conf.d/default.conf`.

## Instructions pour installer le projet WordPress
- Installer les dépendances du projet avec la commande `composer install` depuis le container crée avec Dockerfile
- Copier le fichier .env.example vers .env 
- Configurer les accès à la base de données `DB_NAME` nom de la base de données, `DB_USER`, `DB_PASSWORD` utilisateur et mot de passe de la base de données, `DB_HOST` le hostname de votre base de données, qui n'est rien d'autre que le nom du service Mariadb utiliser pour se connecte à la base.
- Remplacer la valeur de `WP_HOME` par http://localhost