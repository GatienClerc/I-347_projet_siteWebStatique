# I-347_projet_siteWebStatique
## Objectif
Site web statique avec Nginx
- Conteneuriser un petit site HTML/CSS.
- Exposer le port 80.
- Ajouter un volume pour modifier le contenu en direct.

## Conception

### Architecture du projet

```text
root
├── web/
│   ├── index.html          # Structure et contenu de la page web
│   └── style.css           # Mise en forme et présentation du site
└── docker-compose.yml      # Configuration des services Docker
```
#### docker-compose.yml
```yml
services:
  web:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - web_data:/usr/share/nginx/html

volumes:
  web_data:
    name: web_data
```

### Fonctionnement

Le site est déployé dans un environnement Docker afin de disposer d'un environnement d'exécution indépendant de la machine utilisée.

Le fonctionnement général est le suivant :

```text
Fichiers HTML/CSS
       │
       ▼
    web_data
       │
       ▼
Conteneur Docker
       │
       ▼
Serveur web
       │
       ▼
http://localhost
```

## Prérequis

Avant de commencer, assurez-vous que **Docker** est installé et démarré sur votre machine.

## Installation

### 1. Se placer à la racine du projet

Ouvrez un terminal **CMD** et placez-vous dans le répertoire racine du projet :

```bash
cd <votre_chemin>
```

### 2. Démarrer les conteneurs Docker

Lancez les conteneurs en arrière-plan à l'aide de la commande suivante :

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

> **Remarque :** les commandes ci-dessus sont prévues pour être exécutées depuis **Windows CMD**.
