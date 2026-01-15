# 🎓 EduGuide - Plateforme d'orientation étudiante propulsée par l'IA

**EduGuide** est une plateforme moderne et intelligente conçue pour aider les étudiant·e·s à s'orienter dans le paysage de l'enseignement supérieur français. Elle combine une base de données robuste d'établissements/carrières avec **Eddy**, un assistant empathique[...] 

---

## 🚀 Fonctionnalités clés 

### 🤖 Assistant d'orientation IA (Eddy)
-   **Discussion en langage naturel** : Posez des questions sur les écoles, les carrières ou des conseils d'orientation.
-   **RAG contextuel** : Eddy utilise un système de "Retrieval Augmented Generation" pour aller chercher des données réelles dans notre base et répondre avec précision.
-   **Accès au web** : Peut naviguer sur le web (de manière sécurisée) pour trouver des informations à jour non présentes dans la base de données.
-   **Sécurité** : Protégé contre les attaques d'injection de prompt et les SSRF.

### 🏫 Explorateur d'écoles & de carrières
-   **Recherche intelligente** : Filtrez les écoles par ville, type (Ingénierie, Commerce, etc.) et domaine.
-   **Visualisation des données** : Graphiques interactifs montrant les perspectives de carrière, les salaires et les statistiques des établissements.
-   **Comparaisons** : Comparez les écoles côte à côte.

### 🛡️ Sécurisé & évolutif
-   **Limitation de débit** : Protège les endpoints API contre les abus.
-   **Protection CORS** : Limite strictement l'accès à l'API au frontend officiel.
-   **Défenses SSRF** : Empêche l'IA d'accéder aux ressources réseau internes.

---

## 🛠️ Stack technique

### Frontend
-   **Framework** : React 18 + Vite
-   **Bibliothèque UI** : Tailwind CSS v4 + Radix UI + Shadcn/UI
-   **Visuels** : Recharts (graphes), Framer Motion (animations), Lucide (icônes)

### Backend
-   **API** : FastAPI (Python 3.9+)
-   **Moteur IA** : Ollama (exécution locale de modèles comme Mistral ou Llama 2/3)
-   **Outils** : BeautifulSoup4 (scraping), Pydantic (validation)
-   **Sécurité** : Middleware personnalisé pour la limitation de débit et la sanitation des entrées

---

## ⚡ Pour commencer

### Prérequis
1.  **Node.js** (v18+) & **npm/pnpm**
2.  **Python** (v3.9+)
3.  **Ollama** : installé et en cours d'exécution.
    -   Installez depuis [ollama.com](https://ollama.com).
    -   Récupérez un modèle : `ollama pull mistral` (ou votre modèle préféré).

### Installation

1.  **Cloner le dépôt** :
    ```bash
    git clone https://github.com/your-repo/eduguide.git
    cd eduguide
    ```

2.  **Installer les dépendances du frontend** :
    ```bash
    npm install
    ```

3.  **Installer les dépendances du backend** :
    ```bash
    cd backend
    pip install -r requirements.txt
    cd ..
    ```

### 🏃‍♂️ Lancer la plateforme

Un script d'aide est fourni pour démarrer le tout en une seule commande :

```bash
./start.sh
```

Ce script va :
1.  Tuer les processus utilisant actuellement les ports 8000 ou 5173.
2.  Démarrer le **backend FastAPI** à `http://localhost:8000`.
3.  Démarrer le **frontend React** à `http://localhost:5173`.

---

## 📂 Structure du projet

```text
.
├── backend/                # Backend Python FastAPI
│   ├── app/                # Logique principale de l'application (API, Agent)
│   ├── models/             # Wrappers clients LLM
│   ├── tools/              # Outils pour l'Agent (Recherche, Scraper)
│   └── data/               # Bases de données JSON (Écoles, Carrières)
├── src/                    # Source du frontend React
│   ├── app/                # Composants fonctionnels (Chatbot, Analytics)
│   ├── components/         # Composants UI partagés
│   └── styles/             # CSS global & configuration Tailwind
├── start.sh                # Script de lancement
└── README.md               # Ce fichier
```

## 🔒 Sécurité

Ce projet met en œuvre plusieurs bonnes pratiques de sécurité :
-   **Validation des entrées** : Les saisies utilisateur sont nettoyées et tronquées.
-   **Garde-fous en sortie** : L'IA est encadrée via des politiques d'utilisation dans le prompt système.
-   **Sécurité réseau** : Le scraper web bloque les plages d'IP privées/locales (protection SSRF).

---
*Créé pour le Bootcamp Chatbot IA d'EPITECH.*
