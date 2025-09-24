# Configuration et installation du pilote Wi-Fi Broadcom sur Manjaro XFCE

Ce guide explique toutes les étapes pour installer et configurer correctement un pilote Wi-Fi Broadcom sur Manjaro XFCE. Il est destiné à être utilisé comme référence si vous réinstallez votre système ou rencontrez le même problème.

---

## 1. Vérifier le noyau Linux

Ouvrez un terminal et tapez :

```bash
uname -r
```

Notez la version du noyau. Par exemple : `6.12.44-3-MANJARO`.

Cette information est nécessaire pour installer le pilote Broadcom correspondant.

---

## 2. Installer le pilote Broadcom correspondant au noyau

Liste des paquets Broadcom disponibles :

```bash
sudo pacman -Ss broadcom
```

Pour un noyau `6.12.x`, installer :

```bash
sudo pacman -S linux612-broadcom-wl
```

> Si vous avez installé précédemment `broadcom-wl-dkms`, désinstallez-le pour éviter les conflits :

```bash
sudo pacman -Rs broadcom-wl-dkms
```

---

## 3. Charger le module du pilote

```bash
sudo modprobe wl
```

Cette commande active le module Broadcom pour votre carte Wi-Fi.

---

## 4. Vérifier la présence de l'interface Wi-Fi

```bash
ip link
```

Vous devriez voir une interface de type `wlp...`, par exemple : `wlp8s0`. Cela signifie que le pilote est correctement chargé.

---

## 5. Vérifier que NetworkManager est actif

```bash
systemctl status NetworkManager
```

Si NetworkManager n'est pas actif :

```bash
sudo systemctl enable --now NetworkManager
```

---

## 6. Scanner les réseaux Wi-Fi disponibles

```bash
nmcli dev wifi list
```

Vous verrez la liste des réseaux Wi-Fi à portée.

---

## 7. Se connecter à un réseau Wi-Fi

```bash
nmcli dev wifi connect "Nom_Du_SSID" password "MotDePasse"
```

Remplacez `Nom_Du_SSID` par le nom exact de votre réseau et `MotDePasse` par votre mot de passe Wi-Fi.

---

## 8. Vérifier la connexion

```bash
nmcli connection show --active
ping -c 3 8.8.8.8
```

Si vous recevez des réponses au ping, votre connexion est active.

---

## 9. Optionnel : Installer l'applet graphique pour XFCE

Pour gérer le Wi-Fi depuis la barre des tâches :

```bash
sudo pacman -S network-manager-applet
```

Ajoutez ensuite `nm-applet` au démarrage automatique de XFCE pour avoir l'icône Wi-Fi visible.

---

**Remarque :**
Ces étapes sont adaptées pour les cartes Broadcom sous Manjaro XFCE et peuvent nécessiter une adaptation si le noyau ou la version de Manjaro change.
