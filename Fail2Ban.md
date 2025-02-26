## Installation et configuration de Fail2ban sur un VPS

### 1\. Installation

Installez Fail2ban sur un serveur Ubuntu/Debian :

```
sudo apt update && sudo apt install fail2ban -y
```

### 2\. Configuration de Fail2ban

Créez un fichier de configuration personnalisé :

```
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

Éditez `jail.local` :

```
sudo nano /etc/fail2ban/jail.local
```

#### Exemple de configuration pour protéger SSH

```
[sshd]
enabled = true
port = 22
maxretry = 5
findtime = 10m
bantime = 1h
    
```

**Explication :**

*   `enabled = true` : Active la protection SSH.
*   `port = 22` : Définit le port surveillé.
*   `maxretry = 5` : Nombre d’échecs avant ban.
*   `findtime = 10m` : Période d’analyse des tentatives.
*   `bantime = 1h` : Durée du bannissement.

### 3\. Activation et gestion de Fail2ban

Démarrer et activer Fail2ban :

```
sudo systemctl enable --now fail2ban
```

Cette commande garantit que Fail2ban se lance automatiquement au démarrage du VPS.

### 4\. Vérification des jails

Voir les jails actives :

```
sudo fail2ban-client status
```

Voir les IP bannies pour SSH :

```
sudo fail2ban-client status sshd
```

### 5\. Gestion des bans

#### Débannir une IP :

```
sudo fail2ban-client set sshd unbanip 192.168.1.100
```

#### Bannir une IP manuellement :

```
sudo fail2ban-client set sshd banip 192.168.1.200
```

### 6\. Modification des options de bannissement

Modifier la durée du bannissement pour toutes les jails :

```
sudo nano /etc/fail2ban/jail.local
```

#### Exemple :

```
[DEFAULT]
bantime = 24h
findtime = 10m
maxretry = 3
    
```

Appliquer les changements :

```
sudo systemctl restart fail2ban
```

### 7\. Démarrage automatique après redémarrage du VPS

Assurez-vous que Fail2ban se lance automatiquement après chaque redémarrage du VPS avec la commande :

```
sudo systemctl enable fail2ban
```

Cette commande enregistre Fail2ban dans le gestionnaire de services pour qu'il démarre automatiquement lors du démarrage du VPS.

### 8\. Vérification de l'état après un redémarrage

Pour vérifier que Fail2ban fonctionne correctement après le redémarrage, utilisez la commande suivante :

```
sudo systemctl status fail2ban
```

Si le service Fail2ban est actif, vous devriez voir quelque chose comme "active (running)" dans le statut.

### 9\. Consulter les logs Fail2ban

Pour vérifier les logs de Fail2ban et voir quelles IP ont été bannies, utilisez :

```
sudo tail -f /var/log/fail2ban.log
```

Cette commande affiche en temps réel les entrées du fichier de log, ce qui peut être utile pour diagnostiquer des problèmes ou voir les tentatives de connexion bloquées.

### 10\. Personnalisation des filtres Fail2ban

Si vous souhaitez créer des filtres personnalisés pour protéger d'autres services, vous pouvez créer un fichier de filtre dans `/etc/fail2ban/filter.d/`.

Exemple pour un service custom nommé "monservice" :

```
[monservice]
enabled = true
port = 12345
filter = monservice
logpath = /var/log/monservice.log
maxretry = 3
bantime = 1h
    
```

Créez le fichier de filtre dans `/etc/fail2ban/filter.d/monservice.conf` pour définir les expressions régulières qui détecteront les tentatives de connexion non autorisées.

### 11\. Ajouter une IP à la liste blanche

Pour ajouter une IP à la liste blanche (ne jamais être bannie), modifiez le fichier `jail.local` :

```
[DEFAULT]
ignoreip = 127.0.0.1/8 ::1 192.168.1.100
```

Cette commande permet à l'IP spécifiée (ici, `192.168.1.100`) de ne jamais être bannie, même si elle échoue plusieurs fois.

### 12\. Personnaliser les actions après un bannissement

Vous pouvez configurer Fail2ban pour envoyer un e-mail lors du bannissement d'une IP. Modifiez la section `[DEFAULT]` de `/etc/fail2ban/jail.local` :

```
[DEFAULT]
action = %(action_mwl)s
```

Cette configuration enverra un e-mail avec des informations détaillées et les logs associés à l'IP bannie.

### 13\. Redémarrer Fail2ban après modification de la configuration

Après avoir modifié les fichiers de configuration ou ajouté des règles personnalisées, vous devez redémarrer Fail2ban pour appliquer les changements :

```
sudo systemctl restart fail2ban
```

### 14\. Supprimer un fichier de configuration ou une règle

Pour supprimer un fichier de configuration de jail (par exemple, un fichier pour SSH), utilisez :

```
sudo rm /etc/fail2ban/jail.d/sshd.conf
```

Redémarrez Fail2ban après pour appliquer la suppression :

```
sudo systemctl restart fail2ban
```

## Résumé des commandes pratiques

*   **Installation de Fail2ban :** `sudo apt update && sudo apt install fail2ban -y`
*   **Créer un fichier de configuration personnalisé :** `sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local`
*   **Édition du fichier de configuration :** `sudo nano /etc/fail2ban/jail.local`
*   **Activer et démarrer Fail2ban :** `sudo systemctl enable --now fail2ban`
*   **Vérifier les jails actives :** `sudo fail2ban-client status`
*   **Voir les IP bannies pour un service spécifique :** `sudo fail2ban-client status sshd`
*   **Débannir une IP :** `sudo fail2ban-client set sshd unbanip 192.168.1.100`
*   **Bannir une IP manuellement :** `sudo fail2ban-client set sshd banip 192.168.1.200`
*   **Vérifier l'état de Fail2ban :** `sudo systemctl status fail2ban`
*   **Redémarrer Fail2ban après modification de configuration :** `sudo systemctl restart fail2ban`
*   **Consulter les logs Fail2ban :** `sudo tail -f /var/log/fail2ban.log`
*   **Voir les actions de Fail2ban en temps réel :** `sudo fail2ban-client status`
*   **Ajouter une IP à la liste blanche :** `ignoreip = 127.0.0.1/8 ::1 192.168.1.100`
*   **Activer Fail2ban au démarrage du VPS :** `sudo systemctl enable fail2ban`
