# Déboguer et Utiliser un Fichier .gitignore

## 1\. Fonctionnement de .gitignore

Le fichier `.gitignore` permet de spécifier quels fichiers et dossiers Git doit ignorer. Cela empêche ces fichiers d'être suivis ou ajoutés au dépôt.

Exemple de contenu typique :

```

.env
/vendor/
/node_modules/
*.log
  
```

## 2\. Vérifier que .gitignore est pris en compte

Assurez-vous que le fichier `.gitignore` est dans la racine de votre projet. Utilisez la commande :

```
ls -a
```

Cela doit afficher `.gitignore` dans la liste.

## 3\. Désindexer les fichiers déjà suivis

Si des fichiers ignorés apparaissent sur GitHub, c'est qu'ils étaient déjà suivis par Git. Utilisez cette commande pour les désindexer :

```
git rm -r --cached .
```

Ensuite, ajoutez à nouveau tous les fichiers pour appliquer le `.gitignore` :

```

git add .
git commit -m "Appliquer le .gitignore"
  
```

## 4\. Vérifier si un fichier est ignoré

Utilisez la commande suivante pour vérifier si un fichier est correctement ignoré :

```
git check-ignore -v <chemin-du-fichier>
```

## 5\. Pousser les changements

Une fois le `.gitignore` corrigé, poussez vos modifications :

```
git push
```

## 6\. Bonnes pratiques

*   Ne suivez jamais des fichiers sensibles comme `.env`.
*   Ajoutez des fichiers générés automatiquement comme `/node_modules/`.
*   Vérifiez vos règles avec `git status` avant de commettre.
