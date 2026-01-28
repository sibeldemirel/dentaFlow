# DentaFlow — Système d'Information pour Laboratoire Dentaire

[![CI](https://img.shields.io/badge/CI-GitHub%20Actions-blue)](#)
[![Snyk](https://img.shields.io/badge/Security-Snyk-red)](#)
[![SonarCloud](https://img.shields.io/badge/Quality-SonarCloud-yellow)](#)
[![License](https://img.shields.io/badge/License-MIT-green)](#)

Résumé
---
DentaFlow est une solution SaaS de gestion de production prothétique dentaire conçue pour l'ère numérique. Elle assure la transition entre les empreintes physiques et les flux CAO/FAO tout en garantissant traçabilité, conformité et intégration d'une visionneuse 3D pour les praticiens.

Table des matières
---
- [Fonctionnalités clés](#fonctionnalit%C3%A9s-cl%C3%A9s)
- [Stack technique](#stack-technique)
- [Conformité & Sécurité](#conformit%C3%A9--s%C3%A9curit%C3%A9)
- [Installation (Développement)](#installation-d%C3%A9veloppement)
- [Lancement rapide](#lancement-rapide)
- [Pipeline CI/CD](#pipeline-cicd)
- [Structure du projet](#structure-du-projet)
- [Contribuer](#contribuer)
- [Contact / Auteur](#contact--auteur)
- [Licence](#licence)

Fonctionnalités clés
---
- Gestion multi-flux : réception et traitement d'empreintes silicones et scans intra-oraux (formats STL/OBJ).
- Traçabilité totale : suivi des travaux par QR Code à chaque étape de l'usinage.
- Portail praticien : espace sécurisé pour chirurgiens-dentistes avec visionneuse 3D intégrée (visualisation STL/OBJ).
- Logistique & facturation : génération de devis conformes aux normes CCAM, gestion des stocks (résines, poudres).
- Audit & historique : historique complet des modifications, états et interventions.
- API REST asynchrone pour intégration tiers.

Stack technique
---
- Frontend
  - Framework : Vue.js 3 (Vite)
  - Styles : Tailwind CSS
  - 3D : Three.js (visionneuse STL/OBJ)
  - Tests : Vitest
- Backend
  - Framework : FastAPI (Python, asynchrone)
  - Python : 3.11
  - Tests : Pytest
- Base de données : PostgreSQL 15 (JSONB pour prescriptions et métadonnées)
- Conteneurisation : Docker & Docker Compose
- Sécurité / DevSecOps : GitHub Actions, Snyk, SonarCloud

Versions (exemples)
---
- Vue.js 3.x
- Tailwind CSS 3.x
- Three.js r14xx (remplacer par la version exacte)
- Python 3.11
- PostgreSQL 15

Conformité & sécurité (Privacy by Design)
---
DentaFlow intègre la protection des données dès la conception :
- Données de santé : Hébergement compatible HDS (Hébergeur de Données de Santé).
- Pseudonymisation : utilisation systématique d'UUID v4 pour l'identification des dossiers patients.
- Chiffrement : données chiffrées au repos (AES-256) et en transit (TLS 1.3).
- Contrôle d'accès : authentification forte (MFA) et gestion des rôles (RBAC).
- Logs & audit : conservation des journaux et piste d'audit pour les opérations sensibles.

Installation (Développement)
---
Pré-requis
- Docker et Docker Compose
- (Optionnel) Compte Snyk pour exécuter des scans locaux

Configuration des secrets
```bash
cp .env.example .env
# Éditez .env pour ajouter vos identifiants et variables d'environnement
```

Lancement rapide (local)
```bash
# Cloner le dépôt
git clone https://github.com/sibeldemirel/dentaFlow.git
cd dentaFlow

# Construire et démarrer les services
docker-compose up --build
```

Accès
- API : http://localhost:8000
- Frontend : http://localhost:80

Exécuter les tests
---
Backend
```bash
# depuis le dossier backend/
pytest -q
```

Frontend
```bash
# depuis le dossier frontend/
pnpm install
pnpm test
```

Pipeline CI/CD
---
Le projet utilise des workflows GitHub Actions qui exécutent :
- Analyse de code statique (SonarCloud) pour surveiller la qualité et la dette technique.
- Scan de vulnérabilités (Snyk) sur le code Python et sur l'image Docker.
- Exécution des tests unitaires (Pytest & Vitest).
- Linter / formatters (ex. black, isort, ESLint) selon configuration.

Structure du projet
---
dentaflow/
```
├── .github/workflows/    # Pipelines CI/CD
├── backend/              # API FastAPI (Python)
│   ├── app/              # Logique métier
│   └── tests/            # Tests unitaires & d'intégration
├── frontend/             # Application Vue.js
│   ├── src/components/3d # Visionneuse STL
│   └── src/views/        # Pages du portail
├── docs/compliance/      # Registre RGPD et Analyses d'impact (PIA)
└── docker-compose.yml    # Orchestration des services
```

Bonnes pratiques et sécurité
---
- Ne commitez jamais de secrets dans le dépôt : utilisez des variables d'environnement ou le secret store CI.
- Validez les entrées utilisateurs côté backend et frontend.
- Activez la revue obligatoire des PR pour fusion sur `develop` / `main`.

Contribuer
---
Merci pour votre intérêt ! Flux de contribution recommandé :
1. Créez une branche descriptive depuis `develop` :
   - feat/nom-feature
   - fix/description-bug
2. Ouvrez une Pull Request ciblant `develop`.
3. Décrivez les changements, ajoutez des captures si nécessaire et assignez des reviewers.
4. Passez les tests et corrigez les retours de revue avant fusion.

Contact / Auteur
---
- Mainteneur : Sibel Demirel (ou équipe projet)
- Repo : https://github.com/sibeldemirel/dentaFlow

Licence
---
Ce projet est distribué sous licence MIT — voir le fichier LICENSE pour les détails.
