Installation et utilisation de NVM et Node.js sur Manjaro

1. Création du dossier NVM
   Pour que NVM fonctionne, il faut d'abord créer un dossier où il sera installé :

```
mkdir -p ~/.nvm
```

Ce dossier stockera tous les fichiers nécessaires pour NVM.

2. Téléchargement et installation de NVM
   On utilise curl pour télécharger et exécuter le script officiel de NVM :

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.6/install.sh | bash
```

Ce script effectue les étapes suivantes :

* Télécharge NVM depuis le dépôt Git.
* Clone NVM dans le dossier `~/.nvm`.
* Ajoute les lignes nécessaires dans le fichier `~/.zshrc` pour activer NVM automatiquement à l'ouverture du terminal.

3. Activation de NVM immédiatement
   Pour utiliser NVM sans fermer le terminal, on exécute :

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

Explications :

* `export NVM_DIR="$HOME/.nvm"` : indique à l'ordinateur où se trouve NVM.
* `[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"` : si le fichier `nvm.sh` existe et n'est pas vide, il est chargé pour activer NVM.
* `[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"` : active l'auto-complétion des commandes NVM.

4. Vérification de l'installation de NVM

```
nvm --version
```

Cela doit afficher la version installée (par exemple 0.39.6).

5. Installation de Node.js via NVM
   Pour installer une version spécifique de Node.js (ici la version 22) :

```
nvm install 22
```

Le script télécharge et installe Node.js ainsi que npm. Il crée aussi un alias par défaut pour cette version.

6. Utilisation de Node.js installé
   Pour utiliser cette version de Node.js :

```
nvm use 22
```

Vérification des versions installées :

```
node -v    # Affiche la version de Node.js, par ex. v22.19.0
npm -v     # Affiche la version de npm, par ex. 10.9.3
```

Avec ces étapes, NVM et Node.js sont correctement installés et prêts à l'emploi sur Manjaro.
