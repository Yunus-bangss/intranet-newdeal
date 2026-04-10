# Projet DevOps - Intranet Newdeal

## Examen DevOps L3 IAGE 2026

---

## 1. Gestion du repository

- **Nom du repository** : `intranet-newdeal`
- **URL** : https://github.com/Yunus-bangss/intranet-newdeal
- **Branches créées** :
  - `main` - Branche principale
  - `dev` - Branche développement
  - `prod` - Branche production
- **Collaborateur invité** : moisawade@gmail.com

---

## 2. Personnalisation du site

- **Template utilisé** : Forty by HTML5 UP (licence CCA 3.0)
- **Image Docker de base** : nginx:alpine3.23-slim
- **Nom du projet** : Intranet Newdeal - Ministère de la Communication Sénégal
- **Contenu personnalisé** : Pages HTML adaptées avec le nom "Newdeal"

---

## 3. Pipeline CI sur branche dev

### Jobs configurés :
1. **Build** : Construction de l'image Docker avec nginx:alpine3.23-slim
2. **Security-scan** : Vérification des vulnérabilités (Trivy) et secrets (Gitleaks)
3. **Push** : Envoi de l'image vers Docker Hub
4. **Notify** : Notification du statut

### Déclenchement :
```bash
git checkout dev
git push origin dev
```

---

## 4. Pipeline CD sur branche prod

### Jobs configurés :
1. **Security-scan** : Scan CRITICAL avant déploiement
2. **Deploy** : Déploiement sur ubuntu-latest (port 80)
3. **Notify** : Notification du résultat

### Déclenchement :
```bash
git checkout prod
git push origin prod
```

---

## 5. Évolution du pipeline

- ✅ Image de base : nginx:alpine3.23-slim (version légère)
- ✅ Scan sécurité avec Trivy et Gitleaks
- ✅ Notification (simulation echo)
- ✅ Push vers Docker Hub

---

## 6. Commandes utilisées

```bash
# Clone du repository
git clone https://github.com/Yunus-bangss/intranet-newdeal.git
cd intranet-newdeal

# Création des branches
git checkout -b dev
git checkout -b prod

# Push des branches
git push origin dev
git push origin prod

# Construction locale Docker
docker build -t newdeal-intranet:latest .

# Lancement local
docker run -d -p 80:80 --name newdeal newdeal-intranet:latest
```

---

## 7. Comment tester le projet

### En local :
```bash
docker build -t newdeal-intranet:latest .
docker run -d -p 8080:80 newdeal-intranet:latest
```
Puis ouvrir http://localhost:8080

### Via GitHub Actions :
1. Faire un push sur la branche dev ou prod
2. Aller dans l'onglet **Actions** du repo
3. Vérifier que les jobs sont réussis

---

## 8. Résumé des étapes réalisées

| Étape | Description | Status |
|-------|-------------|--------|
| 1 | Création du repository GitHub | ✅ |
| 2 | Personnalisation du template | ✅ |
| 3 | Configuration Dockerfile | ✅ |
| 4 | Test local Docker | ✅ |
| 5 | Pipeline CI (dev) | ✅ |
| 6 | Pipeline CD (prod) | ✅ |
| 7 | Scan sécurité (Trivy + Gitleaks) | ✅ |
| 8 | Push Docker Hub | ✅ |

---

## 9. Conclusion

Ce projet démontre la mise en place d'un pipeline CI/CD complet :
- Build automatique d'une image Docker
- Scan de vulnérabilités et secrets
- Déclenchement sur push GitHub
- Workflow fonctionnel

---

**Étudiant** : Abdou Rahim Younouss Bangoura  
**Date** : 10 Avril 2026