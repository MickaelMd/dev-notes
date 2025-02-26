Qu'est-ce que SQLMap ?
======================

SQLMap est un outil open source de test de pénétration qui permet d'automatiser le processus de détection et d'exploitation des vulnérabilités d'injection SQL dans les applications web. Développé en Python, SQLMap est capable d'interagir avec différents systèmes de gestion de bases de données, notamment MySQL, PostgreSQL, Microsoft SQL Server, Oracle, et SQLite.

Fonctionnalités principales :
-----------------------------

*   **Détection des vulnérabilités :** SQLMap peut identifier automatiquement les paramètres d'une URL qui sont vulnérables à l'injection SQL.
*   **Exploitation des vulnérabilités :** Une fois une vulnérabilité détectée, SQLMap peut l'exploiter pour extraire des données sensibles de la base de données cible.
*   **Support pour plusieurs bases de données :** SQLMap est compatible avec de nombreux systèmes de gestion de bases de données, permettant une grande flexibilité dans les tests de sécurité.
*   **Options avancées :** L'outil propose de nombreuses options pour personnaliser les tests, y compris l'utilisation de proxies, le réglage de la vitesse d'attaque, et la possibilité de charger des scripts personnalisés.
*   **Extraction de données :** SQLMap peut extraire des bases de données, des tables et des colonnes, ainsi que les données qu'elles contiennent.
*   **Support des authentifications :** Il peut gérer divers types d'authentification, y compris les sessions basées sur les cookies et les formulaires d'authentification.

Utilisation éthique :
---------------------

Bien que SQLMap soit un outil puissant pour identifier et exploiter les vulnérabilités, son utilisation doit être éthique et légale. Il est essentiel d'avoir l'autorisation explicite de tester une application web avant de l'utiliser pour éviter toute violation de la loi.

  

* * *

  

Installation de SQLMap via apt
==============================

Ouvrir un terminal :
--------------------

Lancez le terminal de votre distribution Linux.

Mettre à jour votre liste de paquets :
--------------------------------------

Avant d'installer un nouveau logiciel, il est toujours bon de mettre à jour la liste des paquets disponibles :

    sudo apt update

Installer SQLMap :
------------------

Utilisez la commande suivante pour installer SQLMap :

    sudo apt install sqlmap

Vérifier l'installation :
-------------------------

Pour vérifier que SQLMap est bien installé, vous pouvez exécuter la commande suivante :

    sqlmap --version

Cela affichera la version de SQLMap installée.

Utilisation de SQLMap
=====================

Étape 1 : Identifier une cible
------------------------------

Avant de commencer à utiliser SQLMap, vous devez avoir une application web cible vulnérable à l'injection SQL. Cela peut être une application que vous développez, un environnement de test comme DVWA, ou une autre application pour laquelle vous avez l'autorisation de tester.

Étape 2 : Exécuter SQLMap
-------------------------

### Tester une URL :

Pour tester une URL avec un paramètre vulnérable, utilisez la commande suivante dans le terminal :

    sqlmap -u "http://example.com/page.php?id=1"

Remplacez `http://example.com/page.php?id=1` par l'URL que vous souhaitez tester.

### Options de base :

*   `-u`: spécifie l'URL de la cible.
*   `--data`: pour spécifier des données POST si l'application utilise des formulaires.
*   `--cookie`: pour inclure des cookies d'authentification, si nécessaire.

Étape 3 : Analyser les résultats
--------------------------------

SQLMap analysera l'URL fournie et tentera de détecter des vulnérabilités d'injection SQL. Les résultats afficheront :

*   Si une injection SQL est possible.
*   Le type de base de données utilisée (MySQL, PostgreSQL, etc.).
*   Les bases de données disponibles sur le serveur.

Étape 4 : Extraire des données
------------------------------

Pour extraire des données spécifiques, vous pouvez utiliser les commandes suivantes :

### Lister les bases de données :

    sqlmap -u "http://example.com/page.php?id=1" --dbs

### Lister les tables d'une base de données :

    sqlmap -u "http://example.com/page.php?id=1" -D nom_base_de_donnees --tables

### Lister les colonnes d'une table :

    sqlmap -u "http://example.com/page.php?id=1" -D nom_base_de_donnees -T nom_table --columns

### Extraire des données d'une table :

    sqlmap -u "http://example.com/page.php?id=1" -D nom_base_de_donnees -T nom_table -C nom_colonne --dump

Exemples de commandes SQLMap
============================

Exécuter avec un proxy :
------------------------

Si vous utilisez un proxy pour intercepter le trafic, exécutez la commande suivante :

    sqlmap -u "http://example.com/page.php?id=1" --proxy="http://127.0.0.1:8080"

Utiliser un fichier de paramètres :
-----------------------------------

Pour exécuter SQLMap à partir d'un fichier de requête HTTP, utilisez :

    sqlmap -r request.txt

Conclusion
==========

SQLMap est un outil puissant pour détecter et exploiter les vulnérabilités d'injection SQL. Assurez-vous d'utiliser cet outil de manière éthique et responsable, en ayant la permission de tester l'application cible.

Pour plus d'informations sur les fonctionnalités avancées et les options supplémentaires, vous pouvez consulter la [Documentation officielle de SQLMap](http://sqlmap.org/).
