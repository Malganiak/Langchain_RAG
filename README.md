# 🤖 RAG Chatbot avec LangChain & PGVector

Ce projet est un tutoriel pratique démontrant comment construire un système de **RAG (Retrieval-Augmented Generation)** capable de répondre à des questions basées sur des documents PDF non structurés.

Le notebook explore deux architectures différentes pour l'interrogation des données :
1. **Approche Agentique (Agentic RAG) :** Un agent autonome qui décide quand utiliser l'outil de recherche.
2. **Approche Chaîne (RAG Chain) :** Une pipeline optimisée en deux étapes (récupération + génération) en un seul appel LLM.

## 📋 Fonctionnalités

* **Ingestion de Données :** Chargement de documents PDF via `PyPDFLoader`.
* **Découpage (Splitting) :** Utilisation de `RecursiveCharacterTextSplitter` pour optimiser les morceaux de texte.
* **Stockage Vectoriel :** Indexation des données dans une base **PostgreSQL** avec l'extension **PGVector**, utilisant les embeddings OpenAI.
* **Configuration Robuste :** Gestion des paramètres via `Pydantic` et variables d'environnement.
* **Comparaison d'Architectures :** Mise en œuvre d'un Agent vs une Chaîne dynamique.

## 🛠️ Prérequis

Avant de commencer, assurez-vous d'avoir :
* Python 3.10+
* Une clé API **OpenAI**.
* Une instance **PostgreSQL** avec l'extension `vector` installée.

### Démarrage rapide de PostgreSQL (via Docker)
Si vous n'avez pas de base de données PGVector, vous pouvez en lancer une rapidement avec Docker :

```bash
docker run -d \
  --name pgvector-rag \
  -e POSTGRES_USER=langchain \
  -e POSTGRES_PASSWORD=langchain \
  -e POSTGRES_DB=langchain \
  -p 5432:5432 \
  ankane/pgvector
