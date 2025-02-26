## Installation de Docker et déploiement de MailHog sur un VPS

### 1\. Installer Docker

Pour installer Docker sur un VPS sous Ubuntu (ou Debian), exécutez les commandes suivantes :

```
sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
  ```

Après avoir ajouté l'utilisateur au groupe Docker, déconnectez-vous du vps et reconnectez-vous afin que les modifications prennent effet. Vous pouvez vérifier l'installation avec :
```
docker --version
docker run hello-world
 ```

### 2\. Installer MailHog via Docker

L'image officielle `mailhog/mailhog` peut parfois poser des problèmes de téléchargement. Voici deux méthodes pour déployer MailHog :

#### Méthode 1 : Utiliser l'image officielle (si elle est disponible)

```
docker pull mailhog/mailhog:latest
docker run -d -p 1025:1025 -p 8025:8025 mailhog/mailhog
```

Notez que le port **1025** est utilisé pour le serveur SMTP, tandis que l'interface web est accessible sur le port **8025**.

#### Méthode 2 : Construire l'image depuis le code source

Si l'image officielle ne fonctionne pas, vous pouvez construire MailHog localement :

1.  Clonez le dépôt MailHog :
  ```
  git clone https://github.com/mailhog/MailHog.git
  cd MailHog
  ```
    
2.  Construisez l'image Docker :
  ```
  docker build -t mailhog .
  ```
3.  Lancez MailHog en arrière-plan :
  ```
  docker run -d -p 1025:1025 -p 8025:8025 mailhog
  ```
### 3\. Vérifier le fonctionnement de MailHog

Pour vous assurer que MailHog fonctionne correctement, vérifiez que le conteneur est actif :
  ```
  docker ps
  ```

L'interface web est accessible via `http://[adresse_ip_votre_VPS]:8025`.

### Remarques supplémentaires

*   La commande `docker run -d` lance le conteneur en mode détaché, ce qui signifie qu'il continue de fonctionner en arrière-plan même après la fermeture du terminal.
*   Si vous rencontrez des erreurs lors du téléchargement des images (ex : erreur HTTP 500), pensez à vérifier votre connexion, utiliser un miroir Docker (via le fichier `/etc/docker/daemon.json`), ou attendre que le problème soit résolu côté Docker Hub.
*   Il se peut que vous ayez besoin de vous connecter à votre compte Docker (avec `docker login`) pour accéder à des images privées ou en cas de limitations de téléchargement sur Docker Hub.
