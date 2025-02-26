## Commandes Symfony 

### Vérification des prérequis

*   `symfony check:requirements` - Vérifie les prérequis de Symfony.
*   `php -v` - Affiche la version de PHP.
*   `composer --version` - Affiche la version de Composer.
*   `node -v` - Vérifie la version de Node.js.
*   `npm -v` - Vérifie la version de NPM.

### Création et gestion de projet

*   `symfony new MonProjet --webapp` - Crée un projet avec les composants web.
*   `symfony new MonProjet --full` - Crée un projet avec tous les composants recommandés.
*   `composer create-project symfony/skeleton MonProjet` - Crée un projet minimal.
*   `symfony new MonProjet --version="6.4.*" --webapp` - Crée un projet à la version webapp 6.4 
*   `composer install` - Installe les dépendances du projet.
*   `composer update` - Met à jour les dépendances.

### Serveur de développement

*   `symfony serve` - Démarre le serveur local.
*   `symfony serve -d` - Démarre le serveur en arrière-plan.
*   `symfony server:status` - Vérifie le statut du serveur.
*   `symfony server:stop` - Arrête le serveur.
*   `symfony server:log` - Affiche les logs du serveur.

### Installation de composants

*   `composer require symfony/twig-bundle` - Installe Twig.
*   `composer require symfony/maker-bundle --dev` - Installe MakerBundle.
*   `composer require symfony/orm-pack` - Installe Doctrine ORM.
*   `composer require symfony/security-bundle` - Gestion de la sécurité.
*   `composer require symfony/validator` - Validation des données.
*   `composer require symfony/form` - Gestion des formulaires.
*   `composer require symfonycasts/verify-email-bundle` - Vérification des emails.
*   `composer require --dev orm-fixtures fakerphp/faker` - Gestion des fixtures et données fictives.
*   `composer require symfony/asset` - Gestion des assets.
*   `composer require symfony/webpack-encore-bundle` - Intégration de Webpack Encore.
*   `composer require symfony/debug-bundle --dev` - Debug en développement.
*   `composer require symfony/profiler-pack --dev` - Outils de profilage.
*   `composer require easycorp/easyadmin-bundle` - Installe EasyAdmin.
*   `php bin/console make:admin:user` - Ajoute un utilisateur administrateur pour EasyAdmin.
*   `php bin/console security:hash-password` - Génére un mot de passe hashé pour EasyAdmin.

### Commandes de génération (make)

*   `symfony console make:controller NomController` - Crée un contrôleur.
*   `symfony console make:entity NomEntity` - Crée une entité.
*   `symfony console make:crud NomEntity` - Crée un CRUD complet.
*   `symfony console make:form NomForm` - Crée un formulaire.
*   `symfony console make:command NomCommande` - Crée une commande personnalisée.
*   `symfony console make:subscriber NomSubscriber` - Crée un subscriber d'événements.
*   `symfony console make:service NomService` - Crée un service.
*   `symfony console make:user` - Crée une entité utilisateur.
*   `symfony console make:auth` - Génère un système d'authentification.
*   `symfony console make:registration-form` - Formulaire d'inscription.
*   `symfony console make:admin:dashboard` - Crée le tableau de bord EasyAdmin.
*   `symfony console make:admin:crud` - Crée un CRUD EasyAdmin.

### Gestion des bases de données (Doctrine)

*   `php bin/console doctrine:database:create` - Crée la base de données.
*   `php bin/console doctrine:database:drop --force` - Supprime la base.
*   `php bin/console make:migration` - Crée une migration.
*   `php bin/console doctrine:migrations:migrate` - Applique les migrations.
*   `php bin/console doctrine:schema:update --force` - Met à jour le schéma.
*   `php bin/console doctrine:fixtures:load` - Charge les données de test.

### Gestion du cache, logs et environnement

*   `php bin/console cache:clear` - Vide le cache en dev.
*   `php bin/console cache:clear --env=prod` - Vide le cache en production.
*   `php bin/console cache:warmup` - Précharge le cache.
*   `php bin/console log:tail` - Affiche les logs en temps réel.
*   `php bin/console about` - Infos sur le projet.

### Gestion des routes

*   `php bin/console debug:router` - Liste les routes disponibles.
*   `php bin/console router:match /chemin` - Teste une route spécifique.

### Gestion des assets

*   `php bin/console assets:install public/` - Installe les assets.
*   `php bin/console asset:install --symlink` - Crée des liens symboliques pour les assets.
*   `php bin/console asset-map:compile` - Compile la carte des assets (Asset Mapper).
*   `npm run dev` - Compile les assets en développement.
*   `npm run build` - Compile les assets pour la production.
*   `npm run watch` - Surveille et compile automatiquement en dev.
*   `php bin/console asset:install --env=prod` - Installe les assets en production.

### Tests et vérifications

*   `composer require --dev phpunit/phpunit` - Installe PHPUnit.
*   `php bin/phpunit` - Lance les tests.
*   `php bin/phpunit --filter NomDuTest` - Exécute un test spécifique.
*   `php bin/console lint:yaml config/` - Vérifie les fichiers YAML.
*   `php bin/console lint:twig templates/` - Vérifie les templates Twig.

### Divers et utilitaires

*   `php bin/console list` - Liste toutes les commandes.
*   `php bin/console help [commande]` - Aide sur une commande spécifique.
*   `php bin/console debug:container` - Liste les services disponibles.
*   `php bin/console debug:config [bundle]` - Affiche la configuration d'un bundle.
*   `php bin/console debug:autowiring` - Montre les services utilisables avec l'autowiring.
