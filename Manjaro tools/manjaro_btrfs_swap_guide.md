# manjaro_btrfs_swap_guide.md

# Guide d'installation du swap sur Manjaro avec Btrfs

Ce guide explique comment créer un fichier swap fonctionnel sur Manjaro installé avec **Btrfs**. Les commandes sont expliquées étape par étape avec leur rôle et l'intérêt de chaque action.

---

## 1. Vérifier le système de fichiers

Avant de créer un swap, il est important de savoir quel système de fichiers est utilisé. Sur Manjaro, utilisez la commande :

```bash
df -T /
```

* `df` : affiche l'utilisation du disque.
* `-T` : affiche le type de système de fichiers.
* `/` : indique la racine du système.

Si le système de fichiers est **btrfs**, certaines méthodes classiques pour créer un swap ne fonctionneront pas.

---

## 2. Créer un swapfile adapté à Btrfs

Sur Btrfs, les fichiers swap doivent être créés avec une commande spéciale pour assurer l'alignement et désactiver le CoW (Copy-on-Write).

```bash
sudo btrfs filesystem mkswapfile -s 10G /swapfile
```

* `sudo` : exécute la commande en superutilisateur.
* `btrfs filesystem mkswapfile` : crée un fichier swap compatible Btrfs.
* `-s 10G` : définit la taille du swap à 10 Go.
* `/swapfile` : chemin du fichier swap.

Cette commande crée un fichier de swap correctement aligné et prêt à être utilisé.

---

## 3. Restreindre les permissions du swapfile

Pour des raisons de sécurité, seul root doit pouvoir lire et écrire dans ce fichier :

```bash
sudo chmod 600 /swapfile
```

* `chmod 600` : permissions lecture/écriture pour le propriétaire uniquement.
* `sudo` : nécessaire pour modifier les permissions d'un fichier root.

---

## 4. Activer le swapfile

Une fois le fichier créé et sécurisé, on peut l'activer :

```bash
sudo swapon /swapfile
```

* `swapon` : active le fichier ou la partition swap.
* `/swapfile` : le fichier swap à activer.

Vérification :

```bash
swapon --show
```

ou

```bash
free -h
```

Ces commandes montrent que le swap est actif et sa taille disponible.

---

## 5. Ajouter le swapfile dans `/etc/fstab` pour l'activer au démarrage

Pour que le swap soit actif automatiquement à chaque démarrage :

```bash
sudo nano /etc/fstab
```

Ajoutez à la fin du fichier :

```
/swapfile none swap defaults 0 0
```

* `/swapfile` : chemin vers le fichier swap.
* `none` : point de montage inutile pour swap.
* `swap` : type de système.
* `defaults` : options par défaut.
* `0 0` : pas de dump ni fsck.

Enregistrez et quittez l'éditeur.

Vérification immédiate sans redémarrage :

```bash
sudo mount -a
swapon --show
```

---

## 6. Résumé des commandes utilisées

```bash
# Vérifier le type de filesystem
df -T /

# Créer le swapfile sur Btrfs
sudo btrfs filesystem mkswapfile -s 10G /swapfile

# Restreindre les permissions
sudo chmod 600 /swapfile

# Activer le swap
sudo swapon /swapfile

# Vérifier l'activation
swapon --show
free -h

# Ajouter au démarrage
sudo nano /etc/fstab
# Ajouter /swapfile none swap defaults 0 0
sudo mount -a
swapon --show
```

Avec cette méthode, le swap de 10 Go est fonctionnel sur Btrfs, sécurisé et actif automatiquement à chaque démarrage.
