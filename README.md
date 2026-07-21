# 🚀 NotificationHub

![.NET](https://img.shields.io/badge/.NET-10-purple)
![C#](https://img.shields.io/badge/C%23-13-blue)
![Docker](https://img.shields.io/badge/Docker-Containerized-blue)
![Clean Architecture](https://img.shields.io/badge/Architecture-Clean%20Architecture-success)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-orange)

## 📌 Description

**NotificationHub** est une API moderne de gestion et de distribution de notifications développée avec **C# 13 et .NET 10**.

L'objectif du projet est de concevoir une plateforme backend robuste permettant de créer, gérer et envoyer différents types de notifications (email, push, SMS...) via une architecture scalable et orientée événements.

Le projet est conçu comme une application proche d'un environnement de production en appliquant les bonnes pratiques d'architecture logicielle, de sécurité, d'observabilité et de déploiement.

---

# 🎯 Objectifs du projet

Ce projet a pour objectifs de démontrer la maîtrise de :

- Conception d'une API REST moderne avec ASP.NET Core
- Architecture Clean Architecture
- Séparation des responsabilités et principes SOLID
- Communication asynchrone avec RabbitMQ
- Persistance avec MongoDB
- Sécurisation avec JWT
- Conteneurisation Docker
- Observabilité avec OpenTelemetry
- Monitoring via HealthChecks
- Logging structuré avec Serilog
- Automatisation CI/CD avec GitHub Actions

---

# 🏗️ Architecture

Le projet suit les principes de la **Clean Architecture** afin de garantir :

- une forte maintenabilité
- une faible dépendance aux frameworks
- une meilleure testabilité
- une séparation claire des responsabilités


```
src/
│
├── NotificationHub.Api
│   └── Point d'entrée HTTP
│
├── NotificationHub.Application
│   └── Cas d'utilisation métier
│
├── NotificationHub.Domain
│   └── Entités et règles métier
│
├── NotificationHub.Infrastructure
│   └── Accès aux données et services externes
│
└── NotificationHub.Worker
    └── Traitement asynchrone des notifications
```

---

# 🧩 Fonctionnalités

## Gestion des notifications

- Création d'une notification
- Consultation de l'historique
- Gestion des statuts :
  - Pending
  - Processing
  - Sent
  - Failed

## Traitement asynchrone

Les notifications sont publiées dans une file RabbitMQ afin de :

- découpler l'API du traitement
- améliorer la scalabilité
- éviter les traitements longs dans les requêtes HTTP


Architecture simplifiée :

```
Client
  |
  |
ASP.NET Core API
  |
  |
RabbitMQ
  |
  |
Worker Service
  |
  |
Notification Provider
```

---

# 🔐 Sécurité

L'API utilise :

- Authentification JWT
- Autorisation basée sur les rôles
- Validation des entrées utilisateur
- Gestion sécurisée des secrets via variables d'environnement


---

# 🛠️ Stack technique

## Backend

| Technologie | Utilisation |
|-|-|
| C# 13 | Langage principal |
| .NET 10 | Framework |
| ASP.NET Core | API REST |
| Entity Framework Core | ORM |
| FluentValidation | Validation métier |
| xUnit | Tests unitaires |

## Données

| Technologie | Utilisation |
|-|-|
| MongoDB | Stockage des notifications |
| RabbitMQ | Message Broker |

## DevOps

| Technologie | Utilisation |
|-|-|
| Docker | Conteneurisation |
| Docker Compose | Environnement local |
| GitHub Actions | CI/CD |
| OpenTelemetry | Observabilité |
| Serilog | Logs structurés |
| HealthChecks | Monitoring |

---

# 📊 Observabilité

Le projet intègre les outils nécessaires au suivi d'une application moderne :

## Logs

Avec **Serilog** :

- logs structurés JSON
- niveaux de logs configurables
- corrélation des requêtes


## Traces

Avec **OpenTelemetry** :

- suivi des appels HTTP
- suivi des traitements RabbitMQ
- diagnostic des performances


## Health Checks

Endpoints disponibles :

```
GET /health
```

Permet de vérifier :

- disponibilité de l'API
- connexion MongoDB
- disponibilité RabbitMQ

---

# 🐳 Installation locale

## Prérequis

- .NET 10 SDK
- Docker
- Docker Compose


## Cloner le projet

```bash
git clone https://github.com/dockev03/NotificationHub

cd NotificationHub
```


## Démarrer l'environnement

```bash
docker compose up -d
```


Les services démarrés :

| Service | Port |
|-|-|
| API | 8080 |
| MongoDB | 27017 |
| RabbitMQ | 5672 |
| RabbitMQ Management | 15672 |


---

# ⚙️ Configuration

Créer un fichier :

```
.env
```


Exemple :

```env
MONGO_CONNECTION=mongodb://localhost:27017
RABBITMQ_HOST=localhost
JWT_SECRET=my-secret-key
```

⚠️ Les secrets ne doivent jamais être commités dans Git.

---

# 📚 Documentation API

Swagger est disponible :

```
http://localhost:8080/swagger
```

Il permet :

- tester les endpoints
- visualiser les modèles
- utiliser l'authentification JWT

---

# 🧪 Tests

Lancer les tests :

```bash
dotnet test
```

Les tests couvrent :

- règles métier
- services applicatifs
- comportements critiques

---

# 🚀 CI/CD

Le pipeline GitHub Actions réalise :

✅ Restore des dépendances  
✅ Build de la solution  
✅ Exécution des tests  
✅ Analyse qualité  
✅ Construction des images Docker  


---

# 🔮 Évolutions prévues

- [ ] Support Email avec SMTP
- [ ] Support notifications Push
- [ ] Gestion multi-utilisateurs
- [ ] Dashboard administration
- [ ] Retry automatique avec Dead Letter Queue RabbitMQ
- [ ] Déploiement Kubernetes
- [ ] Monitoring Grafana / Prometheus
- [ ] Tests d'intégration complets

---

# 👨‍💻 Auteur

**DocKeV**

Développeur FullStack spécialisé dans l'écosystème Microsoft (.NET), avec un intérêt particulier pour :

- Architecture logicielle
- DevOps
- Cloud Native
- Sécurité applicative
- Automatisation