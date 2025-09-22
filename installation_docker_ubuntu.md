# Installation de Docker sur Ubuntu

Ce guide explique comment installer Docker sur Ubuntu et vérifier son installation.

---

## Étape 1 : Vérifier la version d'Ubuntu

Docker n'est pas compatible avec les anciennes versions d'Ubuntu. Vous devez avoir au minimum :

* Ubuntu Oracular 24.10
* Ubuntu Noble 24.04 (LTS)
* Ubuntu Jammy 22.04 (LTS)

Vous pouvez vérifier les prérequis dans la documentation officielle : [Docker Docs](https://docs.docker.com/engine/install/ubuntu/#prerequisites)

---

## Étape 2 : Désinstaller les anciennes versions

Avant d'installer Docker, supprimez toutes les anciennes versions et les paquets en conflit :

```bash
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

---

## Étape 3 : Installer Docker via APT

### 3.1 Installer les dépendances

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
```

### 3.2 Ajouter la clé GPG officielle de Docker

```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### 3.3 Ajouter le dépôt Docker

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### 3.4 Installer Docker et Docker Compose

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

---

## Étape 4 : Vérifier l'installation

Pour tester si Docker est correctement installé, lancez :

```bash
sudo docker run hello-world
```

Cette commande téléchargera et exécutera l'image `hello-world` pour vérifier que Docker fonctionne correctement.

---

**Installation terminée !** Docker est maintenant prêt à être utilisé sur votre système Ubuntu.
