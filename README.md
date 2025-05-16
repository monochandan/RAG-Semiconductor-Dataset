## RAG pipeline For Semi-conductor manufacturing process

Building a semantic vector search system using sensor data from a semiconductor manufacturing process. The aim is to embed processed sensor logs and store them in a FAISS vector database for efficient similarity search or retrieval-based applications.

## Generating prompts:
Looping through sensor data to create natural language prompts describing the original, processed readings, timestamp, and system status (faulty/not faulty).
## Creating Langchain Object:
Wrapping each prompt in a Document object with metadata (e.g., label: faulty or not faulty).
## Chunking documentation:
Using RecursiveCharacterTextSplitter to split long documents into smaller chunks (~512 characters) for better embedding and indexing.
## Embedding texts:
Using HuggingFaceEmbeddings with the model "sentence-transformers/all-mpnet-base-v2" to embed the document chunks.
## Storing in FAISS Vector DB:
Using FAISS.from_documents(chunk_docs, embedding) to create a FAISS vector store from the document chunks and embeddings.
