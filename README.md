DentaFlow - Système d'Information pour Laboratoire Dentaire

Qu'est-ce que DentaFlow ?
DentaFlow est une solution SaaS de gestion de production prothétique dentaire conçue pour l'ère numérique. Elle assure la transition entre les empreintes physiques et les flux CAO/FAO tout en garantissant une sécurité maximale pour les données de santé.

Fonctionnalités Clés
- Gestion Multi-flux : Réception des empreintes silicones et scans intra-oraux (STL/OBJ).
- Traçabilité Totale : Suivi des travaux par QR Code à chaque étape de l'usinage.
- Portail Praticien : Espace sécurisé pour les chirurgiens-dentistes avec visionneuse 3D intégrée.
- Logistique & Facturation : Génération de devis aux normes CCAM et gestion des stocks de résines/poudres.

Stack Technique
- Frontend : Vue.js (Vite, Tailwind CSS, Three.js pour la 3D).
  - Version :
    - Vue.js 3 : 
    - Tailwind CSS :
    - Three.js : 
- Backend : FastAPI (Python), asynchrone et performant.
  - Version : Python 3.11
- Base de données : PostgreSQL 15 (avec support JSONB pour les prescriptions).
- Infrastructure : Docker & Docker Compose, prêt pour un déploiement certifié HDS.
- DevSecOps : CI/CD via GitHub Actions avec scans Snyk et SonarCloud.

Conformité et Sécurité (Privacy by Design)
DentaFlow intègre la protection des données dès sa conception :
- Données de Santé : Hébergement compatible HDS (Hébergeur de Données de Santé).
- Pseudonymisation : Utilisation systématique d'UUID v4 pour l'identification des dossiers patients.
- Chiffrement : Données chiffrées au repos (AES-256) et en transit (TLS 1.3).
- Contrôle d'accès : Authentification forte (MFA) et gestion des rôles (RBAC).

Installation (Développement)
Pré-requis
  Docker et Docker Compose
  Un compte Snyk (pour les scans de sécurité locaux)

Lancement rapide
Cloner le dépôt :

Bash
git clone https://github.com/votre-repo/dentaflow.git
cd dentaflow
Configurer les secrets :

Bash
cp .env.example .env
# Éditez le fichier .env avec vos identifiants
Démarrer l'infrastructure :

Bash
docker-compose up --build
L'API sera disponible sur http://localhost:8000 et le Frontend sur http://localhost:80.

Pipeline CI/CD
Le projet utilise un workflow GitHub Actions automatisé qui exécute :

L'analyse de code statique (SonarCloud) pour maintenir une dette technique faible.

Le scan de vulnérabilités (Snyk) sur le code Python et l'image Docker.

Les tests unitaires (Pytest & Vitest) pour garantir la non-régression.

Structure du Projet
Plaintext
dentaflow/
├── .github/workflows/    # Pipelines CI/CD
├── backend/              # API FastAPI (Python)
│   ├── app/              # Logique métier
│   └── tests/            # Tests unitaires & intégration
├── frontend/             # Application Vue.js
│   ├── src/components/3d # Visionneuse STL
│   └── src/views/        # Pages du portail
├── docs/compliance/      # Registre RGPD et Analyses d'impact (PIA)
└── docker-compose.yml    # Orchestration des services


🤝 Contribution
Pour toute modification, merci de créer une branche feat/nom-feature à partir de develop et d'ouvrir une Pull Request pour revue.
