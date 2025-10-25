
# 🧠 Activer la compression RAM (ZRAM) sous Manjaro Linux

> **Objectif :** Optimiser la gestion de la mémoire vive (RAM) sur Manjaro grâce à **ZRAM**, pour améliorer la réactivité du système, réduire le swap sur disque, et éviter les lenteurs lorsque la RAM est saturée.

---

## 🔍 1. Qu’est-ce que ZRAM ?

**ZRAM** est une technologie du noyau Linux qui crée un **disque virtuel compressé en mémoire (RAM)**.
Ce disque est utilisé comme **swap**, mais **sans écrire sur le disque dur**, ce qui rend l’opération **plus rapide** et **réduit l’usure du SSD**.

### ⚙️ En résumé :

| Avantage                         | Explication                                                                          |
| -------------------------------- | ------------------------------------------------------------------------------------ |
| 💨 **Vitesse**                   | Le swap se fait directement en mémoire, donc bien plus rapide que sur disque.        |
| 💾 **Moins d’usure**             | Pas de swap sur disque → pas d’écritures inutiles sur SSD.                           |
| 🧩 **Plus de mémoire effective** | Les pages compressées utilisent moins d’espace RAM.                                  |
| ⚡ **Système plus fluide**        | Idéal quand tu travailles avec des outils lourds comme Next.js, Docker, VSCode, etc. |

---

## 🧰 2. Installation du générateur ZRAM

Sur Manjaro (ou Arch), on installe le paquet **`zram-generator`** :

```bash
sudo pacman -S zram-generator
```

📦 Exemple de sortie :

```
Paquets (1) zram-generator-1.2.1-1
:: Procéder à l’installation ? [O/n] o
:: Récupération des paquets…
zram-generator-1.2.1-1-x86_64  332,0 KiB   113 KiB/s 00:03
```

✅ Cela installe le service **systemd** capable de créer et gérer automatiquement un périphérique ZRAM.

---

## 🧩 3. Configuration de ZRAM

Créer le fichier de configuration :

```bash
sudo nano /etc/systemd/zram-generator.conf
```

Puis ajoute ce contenu :

```ini
[zram0]
zram-size = ram / 2
compression-algorithm = zstd
swap-priority = 100
fs-type = swap
```

### 🧾 Explication ligne par ligne :

| Option                         | Description                                                                                       |
| ------------------------------ | ------------------------------------------------------------------------------------------------- |
| `zram-size = ram / 2`          | Alloue 50 % de la RAM totale pour le swap compressé. Si tu as 8 Go de RAM → environ 4 Go de ZRAM. |
| `compression-algorithm = zstd` | Utilise l’algorithme de compression **zstd**, rapide et efficace.                                 |
| `swap-priority = 100`          | Donne la priorité au ZRAM avant le swapfile sur disque.                                           |
| `fs-type = swap`               | Spécifie que le périphérique sera utilisé comme espace d’échange (swap).                          |

---

## 🔄 4. Activer le service ZRAM

Recharge systemd :

```bash
sudo systemctl daemon-reload
```

Démarre le service :

```bash
sudo systemctl start systemd-zram-setup@zram0.service
```

Tente d’activer au démarrage :

```bash
sudo systemctl enable systemd-zram-setup@zram0.service
```

🟡 Tu verras peut-être ce message :

> *“The unit files have no installation config...”*

C’est **normal**.
Le service **[systemd-zram-setup@zram0.service](mailto:systemd-zram-setup@zram0.service)** est un **template** (unité dynamique) — il est géré automatiquement, donc pas besoin de l’activer manuellement.

---

## 🔍 5. Vérification

Affiche les périphériques de swap actifs :

```bash
swapon --show
```

Exemple de résultat :

```
NAME       TYPE      SIZE   USED PRIO
/swapfile  file       10G 857,2M   -2
/dev/zram0 partition 3.8G     0B  100
```

🔹 `/dev/zram0` → swap compressé actif
🔹 `/swapfile` → ton ancien swap sur disque

Et pour voir les détails du périphérique ZRAM :

```bash
zramctl
```

Sortie typique :

```
NAME       ALGO   DISKSIZE  DATA  COMPR  TOTAL  STREAMS MOUNTPOINT
/dev/zram0 zstd       4G      0B     0B    12K       4   [SWAP]
```

---

## 💡 (Optionnel) Désactiver le swapfile pour n’utiliser que ZRAM

Si tu veux éviter complètement le swap sur disque :

1. Désactiver le swapfile :

   ```bash
   sudo swapoff /swapfile
   ```

2. Supprimer la ligne du swapfile dans `/etc/fstab` :

   ```bash
   sudo nano /etc/fstab
   ```

   → commente la ligne contenant `/swapfile`.

3. Vérifie :

   ```bash
   swapon --show
   ```

   Tu ne devrais voir que `/dev/zram0`.

---

## ✅ Résultat attendu

Après ces étapes :

* ton système utilise un **swap compressé en RAM** (rapide),
* ton SSD n’est plus sollicité pour le swap,
* les gros projets (Next.js, Docker, etc.) gèlent beaucoup moins,
* tu gagnes en **fluidité** et en **réactivité**.

---

## 📚 Références

* [Arch Wiki – ZRAM](https://wiki.archlinux.org/title/Zram)
* [systemd-zram-generator – GitHub](https://github.com/systemd/zram-generator)
* [Manjaro Forum – Activer zram-generator](https://forum.manjaro.org/)

---

Souhaites-tu que je te crée le **fichier `.md`** prêt à télécharger (`zram-setup-manjaro.md`) avec tout ce contenu formaté proprement ?
