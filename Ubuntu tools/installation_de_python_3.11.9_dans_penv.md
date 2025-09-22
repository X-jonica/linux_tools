# README.md

# Guide d'installation de Python 3.11.9 avec Pyenv (Ubuntu)

Ce guide explique comment installer et configurer Python 3.11.9 sur Ubuntu en utilisant **Pyenv**, tout en conservant la version système de Python.

---

## Étape 1 : Installer les dépendances

Ouvrez un terminal et exécutez :

```bash
sudo apt update
sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev curl llvm
```

---

## Étape 2 : Installer Pyenv

Copiez et collez la commande suivante :

```bash
curl https://pyenv.run | bash
```

---

## Étape 3 : Configurer Pyenv dans le shell

1. Ouvrez le fichier de configuration de votre shell :

   - Pour Bash :

   ```bash
   nano ~/.bashrc
   ```

   - Pour Zsh :

   ```bash
   nano ~/.zshrc
   ```

2. Ajoutez ces lignes à la **fin du fichier** :

```bash
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

3. Sauvegardez (Ctrl+O → Entrée) et quittez (Ctrl+X).
4. Rechargez la configuration :

```bash
source ~/.bashrc   # ou source ~/.zshrc
```

---

## Étape 4 : Installer Python 3.11.9

```bash
pyenv install 3.11.9
```

---

## Étape 5 : Utiliser Python 3.11.9

- Pour l'utiliser dans le dossier courant :

```bash
pyenv local 3.11.9
```

- Pour le définir comme version globale :

```bash
pyenv global 3.11.9
```

- Vérifiez la version :

```bash
python --version  # Doit afficher "Python 3.11.9"
```

---

## Étape 6 : Vérifications finales

- Lister les versions installées :

```bash
pyenv versions
```

- Désinstaller une version :

```bash
pyenv uninstall 3.11.9
```

---

## Notes importantes

- Pyenv permet de gérer plusieurs versions de Python sans conflit.
- La version système de Python (ex: Python 3.10.12) reste intacte.
- Utilisez `python3.11` pour lancer spécifiquement cette version.

---

## En cas de problème

- Erreur "pyenv: command not found" ? Vérifiez les étapes 2 et 3.
- Problème de compilation ? Assurez-vous d'avoir installé toutes les dépendances (étape 1).
