# Installation de Docker et Docker Compose

Ce guide explique comment installer Docker et Docker Compose sur Ubuntu.

**Remarque :** Sauvegardez ce script sous le nom `install_docker.sh` puis exécutez-le.

---

## Étape 1 : Désinstaller les anciennes versions

```bash
sudo apt remove -y docker docker-engine docker.io containerd runc
sudo apt autoremove -y
```

---

## Étape 2 : Installer les dépendances

```bash
sudo apt update
sudo apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    software-properties-common
```

---

## Étape 3 : Ajouter la clé GPG officielle de Docker

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

---

## Étape 4 : Ajouter le dépôt Docker

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

---

## Étape 5 : Installer Docker Engine

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

---

## Étape 6 : Installer Docker Compose

```bash
sudo apt install -y docker-compose-plugin
```

---

## Étape 7 : Vérifier l'installation

```bash
sudo docker --version
sudo docker compose version
```

---

## Étape 8 : Configurer les permissions

Remplacez `$USER` par votre nom d'utilisateur si nécessaire :

```bash
sudo usermod -aG docker $USER
newgrp docker
```

---

## Étape 9 : Tester Docker sans sudo

```bash
docker run hello-world
```

---

**Installation terminée !**

Déconnectez et reconnectez votre session pour que les changements prennent effet.
