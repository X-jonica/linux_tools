INSTALLATION ET GESTION D'APACHE SOUS UBUNTU
===========================================

## 1. Installation d'Apache
---------------------------
1. Mettre à jour la liste des paquets :
```bash
sudo apt update
```

2. Installer Apache2 :
```bash
sudo apt install apache2 -y
```

3. Vérifier qu'Apache est bien installé :
```bash
apache2 -v
```
Cela affichera la version d'Apache installée.

---

## 2. Gestion du service Apache
-------------------------------

### Démarrer Apache
```bash
sudo systemctl start apache2
```

### Arrêter Apache
```bash
sudo systemctl stop apache2
```

### Redémarrer Apache
```bash
sudo systemctl restart apache2
```

### Recharger la configuration sans arrêter le serveur
```bash
sudo systemctl reload apache2
```

### Vérifier le statut du service
```bash
sudo systemctl status apache2
```

---

## 3. Activer/Désactiver Apache au démarrage
--------------------------------------------

### Activer au démarrage
```bash
sudo systemctl enable apache2
```

### Désactiver au démarrage
```bash
sudo systemctl disable apache2
```

---

## 4. Tester Apache
-------------------
1. Ouvrir un navigateur web.
2. Aller sur l'adresse :
```
http://localhost
```
Vous devriez voir la page par défaut d'Apache.

