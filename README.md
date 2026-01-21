# Recipe RAG Assistant

A sophisticated Retrieval-Augmented Generation (RAG) Agent built with Langflow, designed to ingest, process, and query culinary documentation stored in a vector database.

## 🚀 Overview
This agent allows users to upload unstructured recipe documents (PDFs, TXT, etc.), automatically chunks and embeds the content, and provides a conversational interface for querying that data using OpenAI's GPT models and Astra DB.

## 🛠️ Technical Stack
- **Orchestration:** Langflow
- **LLM:** OpenAI (GPT-4o-mini)
- **Vector Database:** DataStax Astra DB
- **Embedding Provider:** NVIDIA (via Astra Vectorize)
- **Document Processing:** Docling-based File Reader & Character Text Splitter

## 🏗️ Architecture
1. **Ingestion Layer:** Reads files and utilizes a `SplitText` component to create overlapping chunks optimized for the NVIDIA embedding model's 512-token limit.
2. **Storage Layer:** Chunks are ingested into an Astra DB collection (`dish_info`) where they are indexed for semantic search.
3. **Retrieval Layer:** The agent performs similarity searches based on user queries, retrieving the most relevant recipe points.
4. **Agentic Layer:** A specialized RAG Agent synthesizes the retrieved information with its internal logic to answer complex culinary questions.

## 🔧 Setup & Configuration
- Ensure your **Astra DB Token** has 'Database Administrator' permissions.
- Configure **OpenAI API Keys** with a positive credit balance.
- Text splitter settings are optimized at a `Chunk Size` of 400 to comply with NVIDIA API limits.
