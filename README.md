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

### Jobs configured :
1. **Build** : Construction de l'image Docker avec nginx:alpine3.23-slim
2. **Scan sécurité** : Vérification des vulnérabilités et secrets
3. **Push** : Envoi de l'image vers Docker Hub

### Déclenchement :
```bash
git checkout dev
git push origin dev
```

---

## 4. Pipeline CD sur branche prod

### Jobs configured :
1. **Security-scan** : Scan CRITICAL avant déploiement
2. **Deploy** : Déploiement sur runner production (port 80)
3. **Notify** : Notification email à moussawade@groupeisi.com

### Déclenchement :
```bash
git checkout prod
git push origin prod
```

---

## 5. Évolution du pipeline

- ✅ Image de base : nginx:alpine3.23-slim (version légère)
- ✅ Bloquer si vulnérabilité CRITICAL détectée
- ✅ Notification email configurée

---

## 6. Commandes utilisées

```bash
# Clone du repository
git clone https://github.com/Yunus-bangss/intranet-newdeal.git
cd intranet-newdeal

# Création des branches
git branch dev
git branch prod

# Push des branches
git push origin dev
git push origin prod

# Construction locale Docker
docker build -t newdeal-intranet:latest .

# Lancement local
docker run -d -p 80:80 --name newdeal newdeal-intranet:latest
```

---

## 7. Résultat des pipelines

| Pipeline | Branche | Status |
|----------|---------|--------|
| CI Pipeline - Dev | dev | ✅ Success |
| CD Pipeline - Prod | prod | ✅ Success |

---

## 8. Étudiant

- **Nom** : Bangoura
- **Prénom** : Abdou Rahim Younouss
- **Email** : abdoucom837@gmail.com

---

## 9. Captures d'écran

(Coller ici les captures d'écran des pipelines GitHub Actions)

---

**Document généré le :** 9 Avril 2026