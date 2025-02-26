## Commandes Symfony

### 🔍 Vérification des prérequis

- `symfony check:requirements` - Vérifie les prérequis de Symfony.
- `php -v` - Affiche la version de PHP.
- `composer --version` - Affiche la version de Composer.
- `node -v` - Vérifie la version de Node.js.
- `npm -v` - Vérifie la version de NPM.

### 🛠️ Création et gestion de projet

- `symfony new MonProjet --webapp` - Crée un projet avec les composants web.
- `symfony new MonProjet --full` - Crée un projet avec tous les composants recommandés.
- `composer create-project symfony/skeleton MonProjet` - Crée un projet minimal.
- `symfony new MonProjet --no-git` - Crée un projet sans initialiser Git.
- `symfony new MonProjet --version="6.4.*" --webapp` - Crée un projet à la version webapp 6.4.
- `composer install` - Installe les dépendances du projet.
- `composer update` - Met à jour les dépendances.

### 🚀 Serveur de développement

- `symfony serve` - Démarre le serveur local.
- `symfony serve -d` - Démarre le serveur en arrière-plan.
- `symfony serve --port=8080` - Démarre le serveur sur un port spécifique.
- `symfony serve --no-tls` - Démarre le serveur sans HTTPS.
- `symfony server:status` - Vérifie le statut du serveur.
- `symfony server:stop` - Arrête le serveur.
- `symfony server:log` - Affiche les logs du serveur.
- `symfony server:ca:install` - Installe le certificat HTTPS auto-signé pour le développement.

### 📦 Installation de composants

- `composer require symfony/twig-bundle` - Installe Twig.
- `composer require symfony/maker-bundle --dev` - Installe MakerBundle.
- `composer require symfony/orm-pack` - Installe Doctrine ORM.
- `composer require symfony/security-bundle` - Gestion de la sécurité.
- `composer require symfony/validator` - Validation des données.
- `composer require symfony/form` - Gestion des formulaires.
- `composer require symfonycasts/verify-email-bundle` - Vérification des emails.
- `composer require --dev orm-fixtures fakerphp/faker` - Gestion des fixtures et données fictives.
- `composer require symfony/asset` - Gestion des assets.
- `composer require symfony/webpack-encore-bundle` - Intégration de Webpack Encore.
- `composer require symfony/debug-bundle --dev` - Debug en développement.
- `composer require symfony/profiler-pack --dev` - Outils de profilage.
- `composer require easycorp/easyadmin-bundle` - Installe EasyAdmin.
- `php bin/console make:admin:user` - Ajoute un utilisateur administrateur pour EasyAdmin.
- `php bin/console security:hash-password` - Génére un mot de passe hashé pour EasyAdmin.

### 📝 Commandes de génération (make)

- `symfony console make:controller NomController` - Crée un contrôleur.
- `symfony console make:entity NomEntity` - Crée une entité.
- `symfony console make:data-fixtures` - Crée une classe de fixtures.
- `symfony console make:crud NomEntity` - Crée un CRUD complet.
- `symfony console make:form NomForm` - Crée un formulaire.
- `symfony console make:command NomCommande` - Crée une commande personnalisée.
- `symfony console make:subscriber NomSubscriber` - Crée un subscriber d'événements.
- `symfony console make:service NomService` - Crée un service.
- `php bin/console make:twig-extension` - Crée une extension Twig personnalisée.
- `symfony console make:user` - Crée une entité utilisateur.
- `symfony console make:auth` - Génère un système d'authentification.
- `symfony console make:registration-form` - Formulaire d'inscription.
- `symfony console make:admin:dashboard` - Crée le tableau de bord EasyAdmin.
- `symfony console make:admin:crud` - Crée un CRUD EasyAdmin.
- `symfony console make:voter NomVoter` - Crée un voter pour la gestion des permissions.
- `symfony console make:event-listener NomListener` - Crée un listener d'événements.
- `symfony console make:event-subscriber NomSubscriber` - Crée un subscriber d'événements.
- `symfony console make:messenger-middleware NomMiddleware` - Crée un middleware pour Messenger.

### 🗄️ Gestion des bases de données (Doctrine)

- `php bin/console doctrine:database:create` - Crée la base de données.
- `php bin/console doctrine:database:drop --force` - Supprime la base.
- `php bin/console make:entity MonEntity` - Crée une entité.
- `php bin/console make:migration` - Crée une migration.
- `php bin/console doctrine:migrations:diff` - Génère une migration en comparant la base de données actuelle et les entités.
- `php bin/console doctrine:migrations:status` - Affiche le statut des migrations.
- `php bin/console doctrine:migrations:execute --up 20230101010101` - Exécute une migration spécifique.
- `php bin/console doctrine:migrations:rollup` - Supprime toutes les migrations et met à jour le schéma directement.
- `php bin/console doctrine:migrations:migrate` - Applique les migrations.
- `php bin/console doctrine:schema:update --force` - Met à jour le schéma.
- `php bin/console doctrine:fixtures:load` - Charge les données de test.
- `php bin/console doctrine:query:sql "SQL"` - Exécute une requête SQL brute.
- `php bin/console doctrine:query:dql "DQL"` - Exécute une requête DQL.
- `php bin/console doctrine:database:import fichier.sql` - Importe un fichier SQL dans la base de données.
- `php bin/console doctrine:cache:clear-metadata` - Vide le cache des métadonnées.
- `php bin/console doctrine:cache:clear-query` - Vide le cache des requêtes.

### ⚙️ Gestion du cache, logs et environnement

- `php bin/console cache:clear` - Vide le cache en dev.
- `php bin/console cache:pool:clear` - Vide un pool de cache spécifique.
- `php bin/console cache:clear --env=prod` - Vide le cache en production.
- `php bin/console cache:warmup` - Précharge le cache.
- `php bin/console log:tail` - Affiche les logs en temps réel.
- `php bin/console about` - Infos sur le projet.
- `php bin/console debug:config [bundle]` - Affiche la configuration d'un bundle.
- `php bin/console debug:container` - Liste les services disponibles.
- `php bin/console debug:dotenv` - Affiche les variables d'environnement chargées.
- `php bin/console debug:autowiring` - Montre les services utilisables avec l'autowiring.

### 🌐 Gestion des routes

- `php bin/console debug:router` - Liste les routes disponibles.
- `php bin/console router:debug --show-aliases` - Affiche les alias de routes.
- `php bin/console router:match /chemin` - Teste une route spécifique.
- `php bin/console router:match --method=POST /chemin` - Teste une route spécifique avec une méthode HTTP particulière.
- `php bin/console debug:router --show-controllers` - Affiche les contrôleurs associés aux routes.

### 🗂️ Gestion des assets

- `php bin/console assets:install public/` - Installe les assets.
- `php bin/console asset:install --symlink` - Crée des liens symboliques pour les assets.
- `php bin/console asset-map:compile` - Compile la carte des assets (Asset Mapper).
- `npm run dev` - Compile les assets en développement.
- `npm run build` - Compile les assets pour la production.
- `npm run watch` - Surveille et compile automatiquement en dev.
- `php bin/console asset:install --env=prod` - Installe les assets en production.
- `php bin/console webpack-encore dev` - Compile avec Webpack en dev.
- `php bin/console webpack-encore production` - Compile avec Webpack en production.

### 🧪 Tests et vérifications

- `composer require --dev phpunit/phpunit` - Installe PHPUnit.
- `php bin/phpunit` - Lance les tests.
- `php bin/phpunit --filter NomDuTest` - Exécute un test spécifique.
- `php bin/console lint:yaml config/` - Vérifie les fichiers YAML.
- `php bin/console lint:twig templates/` - Vérifie les templates Twig.
- `php bin/console security:check` - Vérifie les vulnérabilités.
- `php bin/console lint:xlf translations/` - Vérifie les fichiers de traduction XLF.
- `php bin/console debug:event-dispatcher` - Liste les événements et listeners.
- `php bin/console debug:event-dispatcher --format=json` - Affiche les événements et listeners au format JSON.
- `php bin/console messenger:consume async` - Lance le consumer pour Messenger.
- `php bin/console messenger:failed:show` - Affiche les messages échoués.

### 🚢 Déploiement et production

- `symfony deploy` - Déploie le projet sur SymfonyCloud.
- `symfony deploy --dry-run` - Simule un déploiement sans appliquer de changements.
- `symfony env:vars` - Liste les variables d’environnement.
- `symfony env:set VAR_NAME=value` - Définit une variable d’environnement.
- `php bin/console doctrine:migrations:migrate --no-interaction` - Migration en production.
- `php bin/console cache:clear --env=prod --no-debug` - Vide le cache en prod sans debug.
- `composer install --no-dev --optimize-autoloader` - Installe les dépendances optimisées.

### 🌍 Traductions et internationalisation

- `php bin/console translation:extract fr --force` - Extrait les chaînes traduisibles.
- `php bin/console translation:update fr` - Met à jour les fichiers de traduction.
- `php bin/console translation:push` - Pousse les traductions vers un service de traduction externe.
- `php bin/console translation:pull` - Récupère les traductions depuis un service de traduction externe.

### 🧰 Divers et utilitaires

- `php bin/console list` - Liste toutes les commandes.
- `php bin/console help [commande]` - Aide sur une commande spécifique.
- `php bin/console make:serializer:encoder` - Crée un encodeur pour le serializer.
- `php bin/console make:serializer:normalizer` - Crée un normaliseur.
- `php bin/console doctrine:query:sql "SELECT * FROM table"` - Requête SQL directe.
- `php bin/console about` - Infos générales du projet.
- `php bin/console messenger:setup-transports` - Configure les transports Messenger.
- `php bin/console messenger:failed:retry` - Réessaye les messages échoués.
- `php bin/console make:controller --api` - Crée un contrôleur API.
- `php bin/console debug:messenger` - Debug des transports Messenger.
- `php bin/console make:middleware` - Crée un middleware pour HTTP Kernel.

✅ **Astuce :** Utilise `php bin/console` sans argument pour voir toutes les commandes disponibles !
