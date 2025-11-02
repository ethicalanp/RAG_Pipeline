RAG Pipeline - Document System


A Retrieval-Augmented Generation (RAG) system that enables intelligent question-answering from PDF documents using LangChain, Groq, and vector databases.


## 🏗️ Architecture

### RAG Pipeline Flow
```mermaid
flowchart LR
    A[📚 Documents<br/>PDF, Excel, HTML] --> B[✂️ Split into Chunks<br/>1000 chars, 200 overlap]
    B --> C[🧬 Generate Embeddings<br/>HuggingFace Model]
    C --> D[(💾 Store in Vector DB<br/>FAISS)]
    
    E[❓ User Query] --> F[🧬 Embed Query]
    F --> G[🔍 Search Similar Chunks<br/>Top k=3]
    D --> G
    
    G --> H[📝 Create Prompt<br/>Context + Query]
    H --> I[🤖 LLM Generation<br/>Groq Llama 3.3]
    I --> J[✅ Answer]
    
    style A fill:#bbdefb,stroke:#1976d2,stroke-width:3px
    style B fill:#fff9c4,stroke:#fbc02d,stroke-width:2px
    style C fill:#c5e1a5,stroke:#689f38,stroke-width:2px
    style D fill:#80deea,stroke:#00796b,stroke-width:3px
    style E fill:#f8bbd0,stroke:#c2185b,stroke-width:3px
    style F fill:#c5e1a5,stroke:#689f38,stroke-width:2px
    style G fill:#ffccbc,stroke:#e64a19,stroke-width:2px
    style H fill:#dcedc8,stroke:#558b2f,stroke-width:2px
    style I fill:#a5d6a7,stroke:#388e3c,stroke-width:3px
    style J fill:#ce93d8,stroke:#8e24aa,stroke-width:3px
```

### Key Components

1. **Document Ingestion**: Supports PDF, Excel, HTML, and database sources
2. **Text Chunking**: RecursiveCharacterTextSplitter with 1000 char chunks and 200 char overlap
3. **Embeddings**: HuggingFace sentence-transformers (all-MiniLM-L6-v2)
4. **Vector Storage**: FAISS for efficient similarity search
5. **LLM**: Groq's llama-3.3-70b-versatile for fast, high-quality responses


PDF Document Processing: Load and process multiple PDF files


Intelligent Chunking: Smart text splitting with overlap for context preservation


Vector Search: FAISS-based semantic search for relevant document retrieval


Free & Fast LLM: Powered by Groq's high-speed inference


Local Embeddings: Uses HuggingFace sentence transformers


Multiple Vector Store Options: Support for FAISS and Typesense


Flexible Configuration: Easy to customize chunk sizes and retrieval parameters


![alt text](image.png)


Prerequisites


Python 3.8+


Groq API Key,Typesense API Key