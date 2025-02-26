# Tutoriel : Comment désactiver Asset Mapper dans Symfony

Symfony 6.4 a introduit Asset Mapper comme une alternative moderne pour gérer les ressources front-end. Toutefois, si vous préférez utiliser l'Asset Component classique ou une autre méthode de gestion des assets comme Webpack Encore, vous pouvez désactiver Asset Mapper. Voici un guide complet pour le faire.

---

## Étape 1 : Modifier la configuration du framework

Dans Symfony, l'activation ou la désactivation d'Asset Mapper est gérée via le fichier `framework.yaml`.

1. Ouvrez le fichier `config/packages/framework.yaml`.
2. Ajoutez ou modifiez la clé `asset_mapper` pour la désactiver explicitement :

```yaml
framework:
    asset_mapper: false
```

---

## Étape 2 : Vérifier que l'Asset Component est installé

Lorsque Asset Mapper est désactivé, Symfony utilise l'Asset Component classique pour servir les fichiers statiques. Assurez-vous que ce composant est bien installé.

### Commande pour installer l'Asset Component :

```bash
composer require symfony/asset
```

---

## Étape 3 : Utiliser le répertoire `public/`

Les fichiers statiques (CSS, JavaScript, images) doivent être placés dans le répertoire `public/` pour être accessibles par l'Asset Component.

### Exemple : Ajouter un fichier JavaScript
1. Créez un répertoire pour vos fichiers :
   ```bash
   mkdir -p public/js
   ```

2. Ajoutez un fichier JavaScript :
   ```bash
   echo "console.log('test.js loaded');" > public/js/test.js
   ```

3. Incluez ce fichier dans vos templates Twig avec la fonction `asset()` :
   ```twig
   {% block javascripts %}
       {{ parent() }}
       <script src="{{ asset('js/test.js') }}" defer></script>
   {% endblock %}
   ```

---

## Étape 4 : Supprimer les fichiers résidus d'Asset Mapper (facultatif)

Si vous avez précédemment utilisé Asset Mapper, des fichiers résidus pourraient encore être présents.

1. Supprimez le répertoire `assets/` (utilisé par Asset Mapper) si vous n'en avez plus besoin :
   ```bash
   rm -rf assets/
   ```

2. Supprimez les fichiers de mapping dans `public/assets/` :
   ```bash
   rm -rf public/assets/
   ```

---

## Étape 5 : Tester la configuration

1. Démarrez le serveur Symfony :
   ```bash
   symfony server:start
   ```

2. Accédez à une page qui inclut des fichiers statiques et vérifiez que les fichiers sont correctement chargés.

3. Vérifiez les journaux pour vous assurer qu'il n'y a aucune erreur liée à Asset Mapper :
   ```bash
   tail -f var/log/dev.log
   ```

---

## Alternatives : Utiliser Webpack Encore (Optionnel)

> **Note** : Il est parfois nécessaire de réactiver `asset_mapper` pour pouvoir installer Webpack Encore.


Si vous souhaitez une solution plus avancée pour gérer vos assets, comme le support de ES6+, SCSS ou la minification, utilisez Webpack Encore.

### Installation de Webpack Encore :

```bash
composer require symfony/webpack-encore-bundle
npm install
```

### Configuration de Webpack Encore :
Créez des fichiers dans le répertoire `assets/`, configurez `webpack.config.js`, et utilisez `{{ encore_entry_script_tags('app') }}` dans vos templates.

Pour un guide complet, consultez [la documentation officielle de Webpack Encore](https://symfony.com/doc/current/frontend.html).

---

En suivant ces étapes, vous aurez désactivé Asset Mapper et configuré Symfony pour gérer vos fichiers statiques avec des méthodes classiques ou avancées comme Webpack Encore.

