# README.md

# Guide : Mettre à jour ou modifier le thème de GRUB

Ce guide explique comment installer et appliquer un thème personnalisé pour GRUB sous Linux.

---

## Étape 1 : Activer l’extension “User Themes”

1. Ouvrez l’application **Extensions** de GNOME.
2. Activez l’extension **User Themes** pour pouvoir appliquer des thèmes personnalisés.

---

## Étape 2 : Télécharger un thème GRUB

1. Rendez-vous sur : [GNOME Look GRUB Themes](https://www.gnome-look.org/browse?cat=109&ord=latest)
2. Choisissez la version adaptée à votre langue (par exemple `Archer_cn` pour le français).

---

## Étape 3 : Extraire et copier le thème

1. Décompressez le fichier téléchargé.
2. Ouvrez un terminal et copiez le thème dans le dossier GRUB :

```bash
sudo mkdir -p /usr/share/grub/themes
sudo cp -r Archer_cn /usr/share/grub/themes
```

* La première commande crée le dossier `themes` si nécessaire.

---

## Étape 4 : Configurer GRUB pour utiliser le thème

1. Ouvrez le fichier de configuration GRUB :

```bash
sudo nano /etc/default/grub
```

2. Ajoutez ou modifiez la ligne suivante :

```text
GRUB_THEME="/usr/share/grub/themes/Archer_cn/theme.txt"
```

---

## Étape 5 : Mettre à jour GRUB

Exécutez la commande suivante pour appliquer le thème :

```bash
sudo update-grub
```

---

## Étape 6 : Redémarrer le PC

Redémarrez votre ordinateur pour voir le nouveau thème GRUB appliqué.

---

**Terminé !** Votre GRUB devrait maintenant afficher le thème personnalisé choisi.
