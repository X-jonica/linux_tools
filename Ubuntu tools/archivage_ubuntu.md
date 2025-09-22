# ARCHIVAGE SOUS UBUNTU

## Comment archiver et extraire une archive ?

GRAPHIQUEMENT :

- Utiliser le logiciel **File-Roller**.

## EN LIGNE DE COMMANDE :

Pour les formats `.tar`, `.tar.gz`, `.tgz`, `.tar.bz2`, `.tbz2`, `.tar.xz` :

### Création d'une archive (plusieurs fichiers)

```bash
tar -cvf archive.tar fichier1 fichier2 ...
```

### Création d'une archive à partir d'un dossier

```bash
tar -cvf archivedossier.tar dossier/
```

### Décompression / Extraction d'une archive

```bash
tar -xvf archivedossier.tar
```

→ Désarchive et décompresse.

Créer un dossier pour décompresser si nécessaire :

```bash
mkdir dossier
```

Extraire dans un dossier spécifique :

```bash
tar -xvf archivedossier.tar -C chemin_du_dossier
```

---

## Compression avec Gzip (`.tar.gz`)

### Création

```bash
tar -zcvf votre_archive.tar.gz votre_dossier/
```

### Extraction

```bash
tar -zxvf votre_archive.tar.gz
```

Extraire dans un dossier spécifique :

```bash
tar -xvzf votre_archive.tar.gz -C chemin_du_dossier
```
