## Qu'est-ce que `fetch()` ?

`fetch()` est une méthode native de JavaScript utilisée pour effectuer des requêtes HTTP asynchrones. Elle est principalement utilisée pour récupérer des ressources depuis un serveur (comme des fichiers JSON, HTML, ou des données d'API), mais elle peut aussi être utilisée pour envoyer des données (par exemple via POST, PUT, DELETE, etc.).

Contrairement aux anciennes méthodes comme `XMLHttpRequest`, `fetch()` repose sur des promesses, ce qui permet de gérer de manière plus simple et plus lisible les résultats des requêtes et les erreurs.

### Principes clés de `fetch()`

*   **Asynchrone** : Les requêtes `fetch()` sont asynchrones, ce qui signifie qu'elles ne bloquent pas l'exécution du code pendant que la requête est en cours. Vous pouvez donc exécuter d'autres actions en attendant la réponse du serveur.
*   **Retourne une promesse** : La méthode `fetch()` renvoie une promesse qui se résout lorsque la réponse est reçue. Cela permet d'utiliser les méthodes `.then()` pour traiter la réponse ou `.catch()` pour gérer les erreurs.
*   **Gestion des erreurs** : Bien que `fetch()` ne rejette pas la promesse en cas d'erreur HTTP (comme un statut 404 ou 500), il est important de vérifier si la réponse est correcte (par exemple, en utilisant `response.ok`) pour gérer les erreurs efficacement.

### Exemple simple d'utilisation de `fetch()`

```javascript

fetch("https://jsonplaceholder.typicode.com/todos/1")
  .then((response) => response.json())  // Transformation de la réponse en JSON
  .then((json) => {
    console.log(json);  // Affiche l'objet JSON
  })
  .catch((error) => {
    console.error("Erreur : ", error);  // Gestion des erreurs
  });
```

**Explication :** Cet exemple montre une requête GET à l'URL `https://jsonplaceholder.typicode.com/todos/1`, qui renvoie un seul objet JSON. Le code utilise la méthode `response.json()` pour convertir la réponse en JSON et affiche l'objet dans la console.

### Utilisation avancée avec options

`fetch()` accepte également un deuxième paramètre : un objet contenant des options pour personnaliser la requête, comme la méthode HTTP, les en-têtes, le corps de la requête, etc. Par exemple :

```javascript

fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",  // Méthode HTTP (ici POST)
  headers: {
    "Content-Type": "application/json",  // En-tête pour spécifier le type de contenu
  },
  body: JSON.stringify({
    title: "foo",
    body: "bar",
    userId: 1,
  }),  // Corps de la requête (données envoyées)
})
  .then((response) => response.json())  // Transformation en JSON
  .then((json) => {
    console.log(json);  // Affiche la réponse
  })
  .catch((error) => {
    console.error("Erreur : ", error);  // Gestion des erreurs
  });
```

**Explication :** Ici, une requête POST est envoyée à l'URL `https://jsonplaceholder.typicode.com/posts` avec un corps de requête en JSON. Le contenu du corps est converti en chaîne JSON avec `JSON.stringify()`, et les en-têtes indiquent que le corps de la requête est du JSON.

### Différences entre `fetch()` et les anciennes méthodes

*   `fetch()` est plus moderne et utilise des promesses pour simplifier le code asynchrone par rapport à `XMLHttpRequest`, qui nécessite des rappels et est plus complexe à gérer.
*   Contrairement à `XMLHttpRequest`, `fetch()` ne rejette pas les promesses en cas d'erreur HTTP (comme 404 ou 500), il faut donc vérifier manuellement le statut de la réponse.

En résumé, `fetch()` est une méthode puissante et flexible pour travailler avec des API et des requêtes réseau en JavaScript, et elle simplifie considérablement la gestion des requêtes asynchrones par rapport aux anciennes solutions.

&nbsp;  
___
&nbsp;  


## Voici une explication des différentes façons de traiter les réponses `fetch` dans ces exemples :

### Exemple 1 : Traitement d'un objet JSON unique

```javascript

fetch("https://jsonplaceholder.typicode.com/todos/1")
  .then((response) => response.json())
  .then((json) => {
    console.log(json); // Affiche l'objet complet

    // Parcours et affichage de chaque propriété de l'objet
    for (const key in json) {
      console.log(`${key}: ${json[key]}`);
    }
  })
  .catch((error) => console.error("Erreur : ", error));
  
```

#### Explication :

**Contexte :** L'URL `https://jsonplaceholder.typicode.com/todos/1` retourne un seul objet JSON représentant une tâche, et non un tableau.

**Affichage de l'objet :** `console.log(json);` affiche l'objet entier en une seule fois. Cet objet ressemble à ceci :

```json

{
  "userId": 1,
  "id": 1,
  "title": "delectus aut autem",
  "completed": false
}
  
```

**Utilisation de `for...in` :** La boucle `for...in` est utilisée pour parcourir chaque clé de l'objet (`userId`, `id`, `title`, et `completed`). Cette syntaxe permet d'afficher chaque propriété individuellement sous la forme :

```text

userId: 1
id: 1
title: delectus aut autem
completed: false
  
```

### Exemple 2 : Traitement d'un tableau de JSON

```javascript

fetch("https://jsonplaceholder.typicode.com/posts")
  .then((response) => response.json())
  .then((data) => {
    data.forEach((element) => {
      console.log(element);
    });
  });
  
```

#### Explication : 

**Contexte :** L'URL `https://jsonplaceholder.typicode.com/posts` retourne un tableau d'objets JSON, chacun représentant un article (`post`). Cela ressemble à ceci :

```json

[
  {
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati",
    "body": "quia et suscipit\nsuscipit..."
  },
  {
    "userId": 1,
    "id": 2,
    "title": "qui est esse",
    "body": "est rerum tempore vitae..."
  },
  ...
]
  
```

**Parcours avec `forEach` :** Comme `data` est un tableau, la méthode `forEach` peut être utilisée pour parcourir chaque élément du tableau. Chaque `element` est un objet représentant un article. Le code `console.log(element);` affiche chaque article un par un.

## Autres approches

### 1\. Utilisation de `Object.entries()` pour parcourir un objet

```javascript

fetch("https://jsonplaceholder.typicode.com/todos/1")
  .then((response) => response.json())
  .then((json) => {
    Object.entries(json).forEach(([key, value]) => {
      console.log(`${key}: ${value}`);
    });
  })
  .catch((error) => console.error("Erreur :", error));
  
```

### 2\. Utilisation de `map()` pour manipuler un tableau

```javascript

fetch("https://jsonplaceholder.typicode.com/posts")
  .then((response) => response.json())
  .then((data) => {
    const titles = data.map((post) => post.title); // Récupère seulement les titres
    console.log(titles);
  })
  .catch((error) => console.error("Erreur :", error));
  
```

### 3\. Filtrer les données avec `filter()`

```javascript

fetch("https://jsonplaceholder.typicode.com/posts")
  .then((response) => response.json())
  .then((data) => {
    const userPosts = data.filter((post) => post.userId === 1); // Récupère seulement les posts de l'utilisateur 1
    console.log(userPosts);
  })
  .catch((error) => console.error("Erreur :", error));
  
```

### 4\. Utilisation de `reduce()` pour agréger des données

```javascript

fetch("https://jsonplaceholder.typicode.com/posts")
  .then((response) => response.json())
  .then((data) => {
    const totalPosts = data.reduce((count, post) => count + 1, 0); // Compte le nombre de posts
    console.log(`Nombre total de posts: ${totalPosts}`);
  })
  .catch((error) => console.error("Erreur :", error));
  
```

### 5\. Utilisation de `for...of` pour parcourir un tableau

```javascript

fetch("https://jsonplaceholder.typicode.com/posts")
  .then((response) => response.json())
  .then((data) => {
    for (const post of data) {
      console.log(post);
    }
  })
  .catch((error) => console.error("Erreur :", error));
  
```

## Différences entre les approches

*   **`forEach` vs `for...in` :** `forEach` est utilisé pour parcourir les tableaux et accéder directement à chaque élément du tableau. `for...in` est adapté pour les objets, permettant d'accéder à chaque clé et à sa valeur.
*   **Structure de la réponse :** Dans le premier exemple, la réponse est un objet unique, donc `for...in` est plus approprié pour accéder à chaque propriété. Dans le second exemple, la réponse est un tableau d'objets, donc `forEach` est plus approprié pour accéder à chaque élément du tableau.

En résumé, la méthode de parcours dépend du type de données retournées par l'API : un objet pour `for...in` et un tableau pour `forEach`.


&nbsp;  
___
&nbsp;  


# Fetch avec async/await

## Introduction

Avec l'introduction de `async/await`, le code basé sur `fetch()` devient plus lisible et facile à maintenir.

## Exemple avec `async/await`

```javascript

async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Erreur lors de la récupération des données :', error.message);
  }
}

fetchData();
```

Dans cet exemple, une requête GET est effectuée pour récupérer des données depuis une API. Si une erreur survient (comme un problème réseau ou un statut HTTP non valide), elle est capturée par le bloc `catch`.

## Avantages de `async/await`

*   **Lisibilité :** Le code est linéaire et facile à suivre, proche d'une structure synchrone.
*   **Gestion des erreurs centralisée :** Utilisation de `try...catch` pour regrouper la gestion des erreurs.
*   **Idéal pour les logiques complexes :** Simplifie les fonctions longues impliquant plusieurs étapes asynchrones.

## Exemple avancé : Requête POST avec options

```javascript

async function postData() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        title: 'foo',
        body: 'bar',
        userId: 1,
      }),
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    const data = await response.json();
    console.log('Données créées :', data);
  } catch (error) {
    console.error('Erreur lors de la création des données :', error.message);
  }
}

postData();
```

Ici, une requête POST est envoyée à une API avec un corps de requête JSON. Les options comme `method`, `headers` et `body` permettent de personnaliser la requête.

Cette présentation montre comment utiliser efficacement `fetch()` avec `async/await` pour simplifier la gestion des requêtes HTTP en JavaScript.
