# Déploiement d'un projet Symfony sur un VPS (Sans Docker)

## Prérequis

*   Serveur VPS avec un accès SSH.
*   Système d'exploitation Linux (par exemple, Ubuntu 22.04).
*   Composer installé sur le serveur.
*   Nginx ou Apache configuré pour servir le projet Symfony.

## Étapes de déploiement

### 1\. Connexion au serveur VPS

Connectez-vous à votre serveur via SSH :

```
ssh utilisateur@votre_ip_vps
```

### 2\. Mise à jour du système

Mettez à jour le système pour garantir que tous les paquets sont à jour :

```
sudo apt update && sudo apt upgrade -y
```

### 3\. Installation des dépendances nécessaires

Installez PHP, Nginx (ou Apache), et les extensions PHP requises pour Symfony :

```
sudo apt install -y nginx php8.3-fpm php8.3-cli php8.3-mysql php8.3-xml php8.3-mbstring php8.3-curl php8.3-intl php8.3-zip git unzip
```

### 4\. Installation de Composer

Installez Composer (si ce n'est pas déjà fait) :

```
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```

### 5\. Clonage du projet Symfony

Clonez votre projet depuis le dépôt Git :

```
git clone https://votre-dépôt.git /var/www/votre-projet
```

### 6\. Installation des dépendances du projet

Installez les dépendances du projet avec Composer :

```
cd /var/www/votre-projet
composer install --no-dev --optimize-autoloader
```

Et npm si besoin :

```
npm install
```

### 7\. Configuration des permissions

Ajustez les permissions pour que le serveur web puisse accéder aux fichiers :

```
sudo chown -R www-data:www-data /var/www/votre-projet
```

### 8\. Configuration de Nginx

Créez une configuration Nginx pour votre application Symfony :

```
sudo nano /etc/nginx/sites-available/votre-projet
```

Ajoutez la configuration suivante :

```
server {
    listen 80;
    server_name votre_domaine.com ou ip;

    root /var/www/votre-projet/public;
    index index.php index.html index.htm;

    location / {
      try_files $uri /index.php$is_args$args;
    }

    location ~ ^/index.php(/|$) {
      fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
      include fastcgi_params;
    }

    location ~ \.php$ {
      try_files $uri =404;
    }
}
```

Activez le site et redémarrez Nginx :

```
sudo ln -s /etc/nginx/sites-available/votre-projet /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```

### 9\. Génération des assets

Générez les assets pour la production :

```
php bin/console asset-map:compile --env=prod
```

### 10\. Configurer le domaine

Assurez-vous que votre nom de domaine pointe vers l'adresse IP de votre VPS. Vous pouvez configurer les DNS auprès de votre fournisseur de domaine.

### 11\. Tests

Accédez à votre domaine dans un navigateur pour tester si l'application Symfony est en fonctionnement.

## Configuration de MariaDB

### 1\. Installation de MariaDB

Si MariaDB n'est pas déjà installé, vous pouvez l'installer avec la commande suivante :

```
sudo apt install mariadb-server mariadb-client
```

### 2\. Sécurisation de l'installation de MariaDB

Lancez le script de sécurisation pour MariaDB :

```
sudo mariadb-secure-installation
```

Répondez aux questions pour définir un mot de passe pour le root, supprimer les utilisateurs anonymes et désactiver les connexions root à distance. Vous pouvez choisir de ne pas activer l'authentification unix\_socket si vous souhaitez que les connexions root passent par un mot de passe.

### 3\. Création de la base de données

Connectez-vous à MariaDB pour créer la base de données nécessaire à votre projet Symfony :

```
sudo mysql -u root -p
```

```
CREATE DATABASE symfony_db;
    CREATE USER 'symfony_user'@'localhost' IDENTIFIED BY 'votre_mot_de_passe';
    GRANT ALL PRIVILEGES ON symfony_db.* TO 'symfony_user'@'localhost';
    FLUSH PRIVILEGES;
```
### 4\. Vider le cache

Pour vider le cache de Symfony, utilisez la commande suivante :

```
php bin/console cache:clear --env=prod --no-debug
```

Cette commande supprimera le cache dans l'environnement de production. Vous pouvez également la lancer dans l'environnement de développement en remplaçant \`--env=prod\` par \`--env=dev\`.

### 5\. Mise à jour des schémas de la base de données

Après avoir configuré votre base de données, vous pouvez mettre à jour les schémas avec la commande suivante :

```
php bin/console doctrine:schema:update --force
```

### 6\. Chargement des fixtures (facultatif)

Si vous avez des fixtures à charger, exécutez la commande suivante :

```
php bin/console doctrine:fixtures:load
```
