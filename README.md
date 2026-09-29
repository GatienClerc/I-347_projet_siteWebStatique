# I-347_projet_siteWebStatique

## Prérequis

Avoir Docker installé et démaré.

## Installation

### 1. Se placer à la racine du projet
Ouvrez un terminal CMD puis exécutez :
```bash
  cd <votre_chemin>
```

### 2. Démarrer les conteneurs Docker
```bash
  docker compose up -d
```

### 3. Copier les fichiers du site dans le volume Docker
```bash
  docker run --rm -v web_data:/destination -v "%cd%\web:/source:ro" alpine sh -c "cp -a /source/. /destination/"
```

### 4. Vérifier le fonctionnement du site
Ouvrez votre navigateur et accédez à l'adresse suivante :  
http://localhost:80  
Si l'installation s'est déroulée correctement, votre site web devrait s'afficher.