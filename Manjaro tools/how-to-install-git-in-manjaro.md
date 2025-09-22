# Installation de Git sur Manjaro

Ce guide explique comment installer Git sur une distribution **Manjaro Linux** et vérifier son installation.

---

## Étape 1 : Installer Git

Ouvrez un terminal et tapez la commande suivante :

```bash
sudo pacman -S git
```

* `sudo` : permet d'exécuter la commande avec les privilèges administrateur.
* `pacman` : gestionnaire de paquets de Manjaro/Arch.
* `-S git` : indique que l'on veut **installer le paquet Git**.

Confirmez l'installation si le système vous le demande.

---

## Étape 2 : Vérifier l'installation

Pour s'assurer que Git est correctement installé, tapez :

```bash
git --version
```

* Le terminal doit afficher la version installée de Git, par exemple : `git version 2.42.0`
* Cela confirme que Git est opérationnel sur votre système.

---

## Notes

* Cette méthode fonctionne sur toutes les éditions de Manjaro (XFCE, KDE, GNOME, etc.).
* Après l'installation, vous pouvez configurer Git avec votre nom et email :

```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
```
