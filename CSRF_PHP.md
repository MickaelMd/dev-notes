Qu'est-ce que le CSRF ?
======================

Le CSRF (Cross-Site Request Forgery) est une vulnérabilité de sécurité qui permet à un attaquant d'exécuter des actions non autorisées sur un site web au nom d'un utilisateur authentifié.

### Définition

Le CSRF est une attaque où un utilisateur malveillant exploite la session active d'un utilisateur sur un site web pour envoyer des requêtes non désirées à ce site. Cela peut se produire lorsqu'un utilisateur est connecté à un site et qu'il visite simultanément un site malveillant qui tente d'exécuter des actions sur le premier site.

### Comment ça fonctionne :

1.  L'utilisateur se connecte à un site légitime (par exemple, un site bancaire) et obtient un cookie de session.
2.  Ensuite, l'utilisateur visite un site malveillant qui contient un code (comme une image ou un script) conçu pour envoyer une requête au site légitime.
3.  Étant donné que l'utilisateur est déjà authentifié, le site légitime interprète la requête comme provenant de l'utilisateur et exécute l'action sans vérification.

### Conséquences

Les attaques CSRF peuvent entraîner des actions non intentionnelles, comme le transfert d'argent, la modification de paramètres de compte ou même la suppression de données.


&nbsp;  
___
&nbsp;  


Protection CSRF en PHP
======================

Pour mettre en place la protection contre les attaques CSRF dans une page PHP, vous pouvez suivre ces étapes :

1.  **Générer le jeton CSRF :** Créez une fonction pour générer un jeton aléatoire et sauvegardez-le dans la session.
2.  **Injecter le jeton dans le formulaire :** Ajoutez un champ caché dans votre formulaire HTML pour envoyer le jeton CSRF.
3.  **Vérifier le jeton lors de la soumission du formulaire :** À la réception du formulaire, comparez le jeton soumis avec celui stocké en session.

Exemple de code
---------------

Voici un exemple de code qui illustre ces étapes :

```php
<?php
session_start();

// Fonction pour générer un jeton aléatoire
function generateCsrfToken() {
    return bin2hex(random_bytes(32)); // Génère un jeton de 64 caractères
}

// Vérifier si le jeton CSRF est déjà défini, sinon le générer
if (empty($_SESSION['csrf'])) {
    $_SESSION['csrf'] = generateCsrfToken();
}

// Traitement du formulaire lors de la soumission
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    // Vérifier si le jeton CSRF est valide
    if (hash_equals($_SESSION['csrf'], $_POST['csrf'])) {
        // Le jeton est valide, traiter le formulaire
        echo "Formulaire soumis avec succès!";
        // Ici, vous pouvez traiter les données du formulaire
    } else {
        // Le jeton est invalide
        die('Token CSRF invalide');
    }
}
?>
```
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Formulaire avec CSRF</title>
</head>
<body>
    <form method="POST" action="">
        <!-- Champ caché pour le jeton CSRF -->
        <input type="hidden" name="csrf" value="<?php echo htmlspecialchars($_SESSION['csrf']); ?>">
        
        <!-- Ajoutez ici d'autres champs de votre formulaire -->
        <label for="name">Nom:</label>
        <input type="text" id="name" name="name" required>
        
        <input type="submit" value="Soumettre">
    </form>
</body>
</html>
```

Explication du Code :
---------------------

*   Démarrage de la session : Utilisez `session_start()` pour accéder aux variables de session.
*   Génération du jeton : La fonction `generateCsrfToken` génère un jeton aléatoire.
*   Stockage du jeton : Si le jeton CSRF n'est pas déjà défini dans la session, il est généré et stocké.
*   Traitement du formulaire : Lors de la soumission du formulaire, le code vérifie si le jeton CSRF soumis correspond à celui stocké en session. Si les jetons correspondent, le formulaire est traité. Sinon, un message d'erreur est affiché.
*   Injection dans le formulaire : Le jeton est inclus dans le formulaire via un champ caché.

Sécurité Additionnelle :
------------------------

*   Utilisez `hash_equals` pour comparer les jetons, ce qui protège contre les attaques par temporisation.
*   Configurez vos cookies pour qu'ils ne soient pas accessibles par JavaScript (option HttpOnly).
*   Implémentez d'autres mesures de sécurité comme la validation des entrées utilisateur pour renforcer la sécurité de votre application.

Avec cela, votre page PHP sera protégée contre les attaques CSRF.
