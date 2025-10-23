# MongoDB and MongoDB Compass Installation on Manjaro

## 🛠️ Installation de MongoDB sur Manjaro

1. Assure-toi que ton système est à jour :

```bash
sudo pacman -Syu
```

2. Installe `yay` si ce n'est pas déjà fait :

```bash
sudo pacman -S yay
```

3. Installe MongoDB depuis l'AUR :

```bash
yay -S mongodb-bin
```

Ce paquet contient les binaires précompilés de MongoDB, ce qui simplifie l'installation : [aur.archlinux.org](https://aur.archlinux.org/packages/mongodb-bin)

4. Démarre et active le service MongoDB :

```bash
sudo systemctl start mongodb
sudo systemctl enable mongodb
```

5. Vérifie que MongoDB fonctionne correctement :

```bash
sudo systemctl status mongodb
```

Tu devrais voir un message indiquant que le service est actif (running).

6. Lance le shell MongoDB :

```bash
mongo
```

Si tu accèdes à l'invite de commande MongoDB, l'installation est réussie.

## 🖥️ Installation de MongoDB Compass sur Manjaro

1. Installe MongoDB Compass depuis l'AUR :

```bash
yay -S mongodb-compass-bin
```

Ce paquet contient le binaire officiel de MongoDB Compass pour Linux.

2. Lance MongoDB Compass depuis le menu des applications ou via le terminal :

```bash
mongodb-compass
```

3. Connecte-toi à ton instance MongoDB locale ou distante et commence à utiliser l'interface graphique pour gérer tes bases de données.
