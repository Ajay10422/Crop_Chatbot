# Agri-Tech Knowledge Retrieval System (RAG Pipeline)

![Python](https://img.shields.io/badge/Python-3.9-3776AB?logo=python&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-Orchestration-green)
![OpenAI](https://img.shields.io/badge/LLM-GPT--3.5-412991?logo=openai&logoColor=white)
![FAISS](https://img.shields.io/badge/Vector_DB-FAISS-00ADD8)
![Streamlit](https://img.shields.io/badge/Frontend-Streamlit-FF4B4B?logo=streamlit&logoColor=white)

## 📌 Project Overview
[cite_start]This repository implements a **Retrieval-Augmented Generation (RAG)** system designed to provide specialized technical assistance to farmers[cite: 7]. [cite_start]Unlike generic chatbots, this system is engineered to answer domain-specific queries by retrieving context from a structured agricultural dataset before generating a response[cite: 4, 5].

[cite_start]The system solves the "hallucination" problem of standard LLMs by grounding answers in verified crop data, aiding farmers in making data-driven decisions regarding crop health and management[cite: 8].

## 🏗️ System Architecture
[cite_start]The application utilizes a **RAG (Retrieve, Augment, Generate)** methodology[cite: 20]. It bridges the gap between the user interface and the underlying data using LangChain orchestration.

```mermaid
graph LR
    %% Definitions
    User[User Query] -->|Input| UI(Streamlit Interface)
    UI -->|Query| Orch{LangChain Orchestrator}
    
    %% RAG Flow
    Orch -->|1. Semantic Search| FAISS[(FAISS Vector Store)]
    FAISS -.->|Embeddings| Data["Crop Dataset (CSV)"]
    FAISS -->|2. Retrieve Context| Orch
    
    Orch -->|3. Prompt + Context| LLM[OpenAI GPT-3.5]
    LLM -->|4. Generate Answer| UI
    
    %% Styling
    style User fill:#f9f,stroke:#333,stroke-width:2px
    style UI fill:#ff4b4b,stroke:#333,stroke-width:2px,color:white
    style Orch fill:#2e8555,stroke:#333,stroke-width:2px,color:white
    style FAISS fill:#00ADD8,stroke:#333,stroke-width:2px,color:white
    style LLM fill:#412991,stroke:#333,stroke-width:2px,color:white
    style Data fill:#e1e1e1,stroke:#333,stroke-width:2px,stroke-dasharray: 5 5

```

🚀 Key Engineering Features

Vector Search & Embeddings: Utilizes FAISS (Facebook AI Similarity Search) to index agricultural data, enabling high-performance semantic search rather than simple keyword matching.


Prompt Engineering: Implements custom prompt templates to instruct the OpenAI GPT-3.5 model to prioritize retrieved context over general knowledge.


Hybrid Query Logic:


Domain Queries: If the input relates to crops, the system retrieves specific answers from the dataset.


General Queries: Falls back to the base LLM capabilities for non-technical conversation.


Interactive UI: Deployed using Streamlit for a responsive, low-latency user experience.

🛠️ Tech Stack

LLM: OpenAI GPT-3.5 


Orchestration: LangChain 


Vector Database: FAISS 


Data Source: Kaggle Agricultural Dataset (CSV: Question/Answer/Crop) 


Frontend: Streamlit 
Launch App

Bash

streamlit run app.py
