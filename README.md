# Projet DevOps - Intranet Newdeal

## Introduction

Ce projet est un site intranet statique développé dans le cadre du cours DevOps CI/CD. Il utilise un template HTML5 UP et est déployé via Docker et GitHub Actions.

---

## 1. Présentation du projet

- **Nom du projet** : Newdeal Intranet
- **Étudiant** : Abdou Rahim Younouss Bangoura
- **Template utilisé** : Forty by HTML5 UP (licence CCA 3.0)
- **Technologies** : HTML, CSS, Docker, GitHub Actions

---

## 2. Structure des fichiers

```
intranet-newdeal/
├── index.html          # Page d'accueil
├── landing.html        # Page landing
├── generic.html        # Page générique
├── elements.html       # Page éléments
├── Dockerfile          # Configuration Docker
├── assets/             # CSS, JS, images
│   ├── css/
│   ├── js/
│   ├── sass/
│   └── webfonts/
├── images/             # Images du site
└── .github/
    └── workflows/
        └── ci-cd.yml   # Pipeline CI/CD
```

---

## 3. Personnalisation effectuée

### Dans index.html :
- Titre : "Newdeal - Intranet"
- Nom : "Abdou Rahim Younouss Bangoura"
- Menu : Accueil, Services, À propos, Contact
- Tuiles : Documents, Équipe, Projets, Actualités, Ressources, Support
- Coordonnées : contact@newdeal.intra, +224 612 00 00 00, Conakry

---

## 4. Configuration Docker

### Dockerfile :
```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/
COPY elements.html /usr/share/nginx/html/
COPY generic.html /usr/share/nginx/html/
COPY landing.html /usr/share/nginx/html/
COPY assets /usr/share/nginx/html/assets
COPY images /usr/share/nginx/html/images

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

### Commandes Docker locales :

```bash
# Construction de l'image
docker build -t newdeal-intranet:latest .

# Lancement du conteneur
docker run -d -p 8080:80 --name newdeal newdeal-intranet:latest

# Arrêt et suppression
docker stop newdeal && docker rm newdeal
```

---

## 5. Configuration GitHub Actions

### Fichier : .github/workflows/ci-cd.yml

```yaml
name: Build and Deploy

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Build Docker image
        run: |
          docker build -t newdeal-intranet:latest -f Dockerfile .
          docker images
```

### Fonctionnement :
1. À chaque `git push` sur la branche `main`, le workflow se déclenche automatiquement
2. Il checkout le code depuis GitHub
3. Il build l'image Docker
4. Si réussi = ✅ (vert)

---

## 6. Commandes Git utilisées

```bash
# Initialisation du repo local
git init
git add .
git commit -m "Initial commit"

# Ajout du remote GitHub
git remote add origin https://github.com/Yunus-bangss/intranet-newdeal.git

# Push vers GitHub
git push -u origin main

# Après modifications
git add .
git commit -m "Description des modifications"
git push origin main
```

---

## 7. Résultat CI/CD

- **Statut** : ✅ Succès (success)
- **Nombre de runs** : 10+
- **Temps de build** : ~13 secondes

---

## 8. Comment tester le projet

### En local :
```bash
docker build -t newdeal-intranet:latest .
docker run -d -p 8080:80 newdeal-intranet:latest
```
Puis ouvrir http://localhost:8080

### Via GitHub Actions :
1. Faire un push sur la branche main
2. Aller dans l'onglet **Actions** du repo
3. Vérifier que le build est réussi (vert)

---

## 9. Résumé des étapes réalisées

| Étape | Description | Status |
|-------|-------------|--------|
| 1 | Création du site HTML | ✅ |
| 2 | Personnalisation (nom, menu, contenu) | ✅ |
| 3 | Configuration Dockerfile | ✅ |
| 4 | Test local Docker | ✅ |
| 5 | Création repo GitHub | ✅ |
| 6 | Configuration GitHub Actions | ✅ |
| 7 | Push et CI/CD automatique | ✅ |

---

## 10. Conclusion

Ce projet démontre la mise en place d'un pipeline CI/CD complet :
- Build automatique d'une image Docker
- Déclenchement sur push GitHub
- Workflow simple et fonctionnel

---

**Étudiant** : Abdou Rahim Younouss Bangoura  
**Date** : 9 Avril 2026update
dev update
