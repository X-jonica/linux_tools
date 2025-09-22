# README.md

# Configuration AutoKey pour taper `<` et `>` avec Alt+; et Alt+:

Ce guide explique comment configurer **AutoKey** sur **Manjaro** pour taper les chevrons `<` et `>` via les raccourcis clavier `Alt + ;` et `Alt + :`, tout en gardant `;` et `:` normaux.

---

## Étape 1 : Installer Pamac (si nécessaire)

1. Vérifier si Pamac est installé :

```bash
sudo pacman -S pamac-gtk
```

2. Si le message indique un conflit avec `pamac-gtk3`, accepter de supprimer `pamac-gtk3` en tapant `o`.
3. Confirmer l’installation de `pamac-gtk` en tapant `o`.

---

## Étape 2 : Installer AutoKey depuis l'AUR

1. Installer AutoKey GTK :

```bash
pamac build autokey-gtk
```

2. Confirmer l’installation et suivre les instructions à l’écran.

---

## Étape 3 : Lancer AutoKey

1. Dans le terminal :

```bash
autokey-gtk
```

2. Ou via le menu de votre environnement de bureau.

---

## Étape 4 : Créer les scripts pour les chevrons

### 4.1 Script pour `<`

1. Dans AutoKey → `My Phrases` ou `Scripts` → **New Script**.
2. Nommer le script : `Chevron ouvrant`.
3. Code du script :

```python
keyboard.send_keys("<")
```

4. Assigner le raccourci : `Alt + ;`

### 4.2 Script pour `>`

1. Nouveau script → Nom : `Chevron fermant`.
2. Code :

```python
keyboard.send_keys(">")
```

3. Assigner le raccourci : `Alt + :`

---

## Étape 5 : Tester

* Ouvrir un éditeur de texte ou IDE.
* Appuyer sur `Alt + ;` → `<`
* Appuyer sur `Alt + :` → `>`
* Vérifier que `;` et `:` restent fonctionnels normalement.

---

## Étape 6 : Sauvegarder la configuration

* AutoKey sauvegarde automatiquement vos scripts et raccourcis.
* Assurez-vous de quitter AutoKey via **File → Quit** ou en laissant le service tourner en arrière-plan.

---

**Note :** Cette configuration fonctionne sur Manjaro avec XFCE, KDE, ou GNOME et permet d’utiliser `<` et `>` sans sacrifier les touches `;` et `:`.
