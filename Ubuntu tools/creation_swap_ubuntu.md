# Guide : Création d'un fichier swap de 8 Go sous Ubuntu

## Objectif

- Ajouter 8 Go d'espace d'échange (swap) à ton système Ubuntu.
- Éviter les ralentissements lorsque la RAM est saturée.

---

## Étape 1 : Vérifier si un swap existe déjà

```bash
sudo swapon --show
```

- Si rien ne s'affiche, aucun swap n'est activé.
- Si un swap existe, tu peux le désactiver avec :

```bash
sudo swapoff /chemin/vers/swap
```

---

## Étape 2 : Créer un fichier swap de 8 Go

```bash
sudo fallocate -l 8G /swapfile
```

- `fallocate` crée un fichier vide de 8 Go nommé `/swapfile`.
- Vérifie l'espace disque libre avec `df -h` avant de créer le swap.

---

## Étape 3 : Sécuriser le fichier swap

```bash
sudo chmod 600 /swapfile
sudo mkswap /swapfile
```

- `chmod 600` empêche les autres utilisateurs de lire le swap.
- `mkswap` formate le fichier pour qu'il soit reconnu comme swap.

---

## Étape 4 : Activer le swap temporairement

```bash
sudo swapon /swapfile
```

- Active le swap immédiatement.
- Vérifie avec `free -h` ou `swapon --show`.

---

## Étape 5 : Rendre le swap permanent

Édite le fichier `/etc/fstab` :

```bash
sudo nano /etc/fstab
```

Ajoute la ligne suivante à la fin du fichier :

```
/swapfile none swap sw 0 0
```

- Cette ligne permet au système d'activer automatiquement le swap au démarrage.
- Pour enregistrer dans nano : `Ctrl + O` → `Entrée` → `Ctrl + X`.

---

## Vérification finale

```bash
free -h
swapon --show
```

- Tu devrais voir `8G` dans la ligne `Swap` de `free -h`.
- `swapon --show` affichera `/swapfile`.

---

## Bonus : Optimiser l'utilisation du swap

- Pour éviter que le swap ne s'active trop tôt :

```bash
sudo sysctl vm.swappiness=10
```

- Pour rendre ce réglage permanent :

```bash
echo "vm.swappiness=10" | sudo tee -a /etc/sysctl.conf
```

- Une valeur de `10` (au lieu de `60` par défaut) réduit l'utilisation du swap quand la RAM est peu utilisée.

---

## Terminé !

Ton swap de 8 Go est maintenant opérationnel et optimisé pour un système avec 8 Go de RAM.
