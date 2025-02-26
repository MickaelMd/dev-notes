Qu'est-ce que le fichier .env ?
-------------------------------

Le fichier `.env` est un fichier de configuration utilisé pour stocker des variables d'environnement dans les applications. Il est souvent utilisé dans le développement d'applications web pour gérer des informations sensibles et des paramètres de configuration sans les inclure directement dans le code source.

### Définition

Un fichier `.env` contient des paires clé-valeur qui définissent des variables d'environnement. Ces variables peuvent inclure des informations telles que les identifiants de base de données, les clés API, les mots de passe et d'autres paramètres nécessaires au bon fonctionnement de l'application.

### Comment ça fonctionne :

1.  Lors du démarrage de l'application, une bibliothèque de gestion des environnements (comme `dotenv` en PHP ou Node.js) charge les variables définies dans le fichier `.env`.
2.  Ces variables peuvent ensuite être accédées dans le code de l'application, permettant aux développeurs de personnaliser le comportement de l'application en fonction de l'environnement (développement, production, etc.).
3.  Le fichier `.env` est généralement exclu du contrôle de version (par exemple, via un fichier `.gitignore`) pour protéger les informations sensibles.

### Conséquences

L'utilisation d'un fichier `.env` permet de séparer la configuration de l'application du code, ce qui améliore la sécurité et la flexibilité. Cela aide également à éviter les fuites d'informations sensibles dans les dépôts de code source.

&nbsp;  
___
&nbsp;  

Installer et utiliser un fichier .env en PHP
============================================

Pour installer et utiliser un fichier `.env` en PHP, il est courant d'utiliser une bibliothèque comme **vlucas/phpdotenv** qui facilite la gestion des variables d'environnement. Voici les étapes à suivre pour installer et configurer un fichier `.env` dans un projet PHP :

Étapes d'installation et configuration :
----------------------------------------

### 1\. Installer Composer (si ce n'est pas déjà fait) :

Si tu n'as pas encore installé Composer, tu peux le télécharger depuis [getcomposer.org](https://getcomposer.org).

### 2\. Installer la bibliothèque `vlucas/phpdotenv` :

Dans ton projet, ouvre un terminal à la racine de ton projet et exécute la commande suivante :

    composer require vlucas/phpdotenv

### 3\. Créer un fichier `.env` :

À la racine de ton projet, crée un fichier nommé `.env`. Dans ce fichier, tu peux définir des variables d'environnement, par exemple :

```php
    DB_HOST=localhost
    DB_PORT=3306
    DB_DATABASE=nom_de_la_base
    DB_USERNAME=root
    DB_PASSWORD=mot_de_passe
```

### 4\. Charger les variables d'environnement dans ton projet PHP :

Dans ton fichier PHP principal (par exemple, `index.php`), tu dois charger et utiliser les variables de ton fichier `.env`. Voici un exemple de code :

```php
    <?php
    require 'vendor/autoload.php';
    
    use Dotenv\Dotenv;
    
    // Charger le fichier .env
    $dotenv = Dotenv::createImmutable(__DIR__);
    $dotenv->load();
    
    // Utiliser une variable d'environnement
    $dbHost = $_ENV['DB_HOST'];
    $dbPort = $_ENV['DB_PORT'];
```

### 5\. Accéder aux variables d'environnement :

Une fois le fichier `.env` chargé, tu peux accéder aux variables définies via `$_ENV` ou `getenv()` :
```php
    echo $_ENV['DB_DATABASE']; // ou
    echo getenv('DB_DATABASE');
```
### Attention :

Ne pas oublier d'ajouter ton fichier `.env` dans le fichier `.gitignore` si tu utilises Git, pour éviter de partager des informations sensibles (comme les mots de passe) :

    .env

Avec cette configuration, tu seras capable de gérer tes configurations d'application via des variables d'environnement dans PHP.

&nbsp;  
___
&nbsp;  

Utilisation du fichier `.env` avec Symfony
==========================================

Dans Symfony, la gestion des variables d'environnement via un fichier `.env` est intégrée de base. Voici comment cela fonctionne :

1\. Le fichier `.env`
---------------------

Lorsque tu crées un projet Symfony, un fichier `.env` est généré automatiquement à la racine du projet. Ce fichier contient déjà certaines variables d'environnement par défaut. Voici un exemple de ce que tu peux y trouver :
```php
    # Exemple de configuration dans un fichier .env
    APP_ENV=dev
    APP_SECRET=some_random_value
    DATABASE_URL="mysql://root:password@127.0.0.1:3306/nom_de_la_base?serverVersion=5.7"
```

2\. Accès aux variables d'environnement
---------------------------------------

Les variables définies dans le fichier `.env` sont automatiquement chargées par Symfony. Dans ton code Symfony, tu peux y accéder via `$_ENV` ou en utilisant `getenv()`.

3\. Utilisation des variables dans les fichiers de configuration
----------------------------------------------------------------

Symfony te permet également d'utiliser les variables d'environnement directement dans les fichiers de configuration YAML. Par exemple, voici comment tu pourrais utiliser la variable `DATABASE_URL` dans le fichier `config/packages/doctrine.yaml` :

```yaml
    doctrine:
        dbal:
            url: '%env(resolve:DATABASE_URL)%'
```

4\. Fichiers `.env` spécifiques aux environnements
--------------------------------------------------

Symfony supporte plusieurs fichiers `.env` pour différents environnements. Par exemple :

*   `.env` : Configuration par défaut pour tous les environnements.
*   `.env.local` : Surcharges pour ton environnement local.
*   `.env.prod` : Spécifique à l'environnement de production.

5\. Système de cache
--------------------

En production, Symfony met en cache les variables d'environnement dans un fichier `.env.local.php` pour éviter de lire le fichier `.env` à chaque requête, améliorant ainsi les performances.

6\. Exemple d'utilisation dans un contrôleur Symfony
----------------------------------------------------

Voici un exemple d'utilisation des variables d'environnement dans un contrôleur Symfony :

```php
    // Dans un contrôleur Symfony
    namespace App\Controller;
    
    use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
    use Symfony\Component\HttpFoundation\Response;
    
    class MyController extends AbstractController
    {
        public function index(): Response
        {
            // Accéder à une variable d'environnement (par exemple, APP_ENV)
            $appEnv = $_ENV['APP_ENV'];
    
            return new Response("L'environnement de l'application est : " . $appEnv);
        }
    }
```

Ainsi, avec Symfony, tout est déjà en place pour gérer facilement tes variables d'environnement via le fichier `.env`.
