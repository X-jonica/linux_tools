# README.md

# Installation de Node.js sur Manjaro

Ce guide explique comment installer **Node.js** et **npm** sur Manjaro Linux en utilisant les dépôts officiels.

---

## Étape 1 : Installer Node.js et npm

Ouvrez un terminal et tapez la commande suivante :

```bash
sudo pacman -S nodejs npm
```

* `sudo` : exécute la commande avec les privilèges administrateur.
* `pacman` : gestionnaire de paquets de Manjaro/Arch.
* `nodejs` : paquet Node.js.
* `npm` : gestionnaire de paquets Node.js.

**Remarque :** La version disponible dans les dépôts officiels peut ne pas être la toute dernière LTS, mais elle reste stable.

---

## Étape 2 : Vérifier l'installation

Pour s'assurer que Node.js et npm sont correctement installés, tapez :

```bash
node -v
npm -v
```

* Le terminal doit afficher les versions installées, par exemple :

  * `v20.5.0` pour Node.js
  * `10.3.0` pour npm

---

## Notes

* Cette méthode fonctionne sur toutes les éditions de Manjaro (XFCE, KDE, GNOME, etc.).
* Vous pouvez ensuite installer des paquets Node.js globalement ou localement selon vos projets.
