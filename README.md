# I-347_projet_siteWebStatique

## Prérequis

Avant de commencer, assurez-vous que **Docker** est installé et démarré sur votre machine.

## Installation

### 1. Se placer à la racine du projet

Ouvrez un terminal **CMD** et placez-vous dans le répertoire racine du projet :

```bash
cd <votre_chemin>
```

### 2. Démarrer les conteneurs Docker

Lancez les conteneurs en arrière-plan avec la commande suivante :

```bash
docker compose up -d
```

### 3. Copier les fichiers du site dans le volume Docker

Copiez ensuite les fichiers présents dans le dossier `web` vers le volume Docker `web_data` :

```bash
docker run --rm -v web_data:/destination -v "%cd%\web:/source:ro" alpine sh -c "cp -a /source/. /destination/"
```

### 4. Vérifier le fonctionnement du site

Ouvrez votre navigateur et accédez à l'adresse suivante :

http://localhost

Si l'installation s'est déroulée correctement, le site web devrait s'afficher.

> **Remarque :** les commandes ci-dessus sont prévues pour une utilisation depuis **Windows CMD**.
