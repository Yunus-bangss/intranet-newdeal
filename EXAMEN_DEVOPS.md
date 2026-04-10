# EXAMEN DEVOPS L3 IAGE 2026

## Projet : Intranet Newdeal - Ministère de la Communication Sénégal

---

## Étudiant

- **Nom** : Bangoura
- **Prénom** : Abdou Rahim Younouss
- **Repository** : https://github.com/Yunus-bangss/intranet-newdeal

---

## Résumé du projet

### 1. Gestion du repository
- Repository : intranet-newdeal
- Branches : main, dev, prod
- Collaborateur invité : moisawade@gmail.com

### 2. Personnalisation
- Template : Forty by HTML5 UP
- Image Docker : nginx:alpine3.23-slim
- Site : Intranet Newdeal Sénégal

### 3. Pipeline CI (branche dev)
- Job 1 : Build image Docker (nginx:alpine3.23)
- Job 2 : Scan sécurité (vulnérabilités + secrets)
- Job 3 : Push image vers Docker Hub

### 4. Pipeline CD (branche prod)
- Job 1 : Scan sécurité CRITICAL
- Job 2 : Déploiement sur port 80
- Job 3 : Notification email

---

## Captures d'écran à inclure

### Capture 1 : CI Pipeline - Branche dev
![image-20260409203506517](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20260409203506517.png)

### Capture 2 : CD Pipeline - Branche prod
![image-20260409203528683](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20260409203528683.png)

---

## Résultat

| Pipeline | Branche | Status |
|----------|---------|--------|
| CI Pipeline - Dev | dev | ✅ Success |
| CD Pipeline - Prod | prod | ✅ Success |

