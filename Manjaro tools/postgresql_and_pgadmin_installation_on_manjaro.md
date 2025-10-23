# PostgreSQL and pgAdmin Installation on Manjaro

## 🛠️ Installation de PostgreSQL

1. Assure-toi que ton système est à jour :

```bash
sudo pacman -Syu
```

2. Installe PostgreSQL :

```bash
sudo pacman -S postgresql
```

3. Initialise la base de données :

```bash
sudo -iu postgres initdb -D /var/lib/postgres/data
```

4. Démarre et active le service PostgreSQL :

```bash
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

5. Vérifie que PostgreSQL fonctionne correctement :

```bash
sudo systemctl status postgresql
```

Tu devrais voir un message indiquant que le service est actif (running).

6. Se connecter au shell PostgreSQL :

```bash
sudo -iu postgres psql
```

Pour quitter le shell : `\q`

---

## 🖥️ Installation de pgAdmin

1. Installer pgAdmin depuis l’AUR :

```bash
yay -S pgadmin4
```

Cela installe pgAdmin 4 (interface web graphique) pour Linux.

2. Lancer pgAdmin :

```bash
pgadmin4
```

Ou depuis le menu des applications.

3. Créer un utilisateur administrateur lors du premier lancement (email + mot de passe).

4. Se connecter à un serveur PostgreSQL :

* Nom du serveur : `local` ou autre
* Hôte : `localhost`
* Utilisateur : `postgres`
* Mot de passe : celui défini pour l’utilisateur PostgreSQL

---

### 💡 Astuces

* Tu peux gérer plusieurs bases de données graphiquement dans pgAdmin.
* PostgreSQL fonctionne en service, donc tu n’as pas besoin de le relancer à chaque fois.
