## Installation de Visual Studio Code sous Manjaro

Sous Manjaro (basé sur Arch Linux), il existe deux façons principales d’installer VS Code. 
Le choix dépend de ce que tu veux privilégier : la version open source ou la version officielle de Microsoft.

------------------------------------------------------
Option 1 : Installer `code` via pacman (open source)
------------------------------------------------------

Commande :
    sudo pacman -S code

✔ Avantages :
- C’est la version open source (basée sur VS Code OSS).
- Disponible directement dans les dépôts Manjaro/Arch.
- Plus intégrée au système et maintenue par la communauté.

❌ Inconvénients :
- Pas exactement la version Microsoft (logo différent, pas toutes les extensions intégrées par défaut).
- Les mises à jour peuvent parfois arriver un peu plus tard que chez Microsoft.

------------------------------------------------------
Option 2 : Installer `visual-studio-code-bin` via AUR (officiel Microsoft)
------------------------------------------------------

Commande :
    yay -S visual-studio-code-bin

✔ Avantages :
- C’est la version officielle de Microsoft (logo, fonctionnalités et extensions complètes).
- Mises à jour directement fournies par Microsoft.
- Support des extensions propriétaires.

❌ Inconvénients :
- Provient de l’AUR, nécessite `yay` ou un autre helper AUR.
- Installation légèrement plus longue (compilation/conversion).

------------------------------------------------------
💡 Recommandation :
- Si tu veux **la version Microsoft avec tout inclus**, installe `visual-studio-code-bin`.
- Si tu veux **une version plus "libre" et communautaire**, installe `code` via pacman.

⚠️ Conseil : il vaut mieux ne pas garder les deux installés en même temps pour éviter les conflits.
