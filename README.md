## RAG pipeline For Semi-conductor manufacturing process

Building a semantic vector search system using sensor data from a semiconductor manufacturing process. The aim is to embed processed sensor logs and store them in a FAISS vector database for efficient similarity search or retrieval-based applications.

## Prepared sensor log data

Combined raw and scaled sensor readings with timestamp and fault labels into descriptive prompts.

## Created prompts for each data point

Used domain-specific instruction: "You are a semiconductor sensor specialist..."

## Each prompt includes timestamp, raw/processed sensor readings, and fault status.

Wrapped prompts into LangChain Document objects

Added metadata like labels for better filtering/search.

## Chunked long prompts into smaller texts

Used RecursiveCharacterTextSplitter to ensure embedding model can handle input size efficiently.

## Generated vector embeddings

Used HuggingFaceEmbeddings (all-mpnet-base-v2) to convert text chunks into dense vectors.

## Created a FAISS vector store

Stored embeddings + texts in FAISS for efficient similarity search.

## Built a retriever

Configured faiss.as_retriever() with similarity search (e.g., top-4 matches).

## Planned to use Zephyr-7B LLM

To generate final answers from retrieved chunks (RAG-style pipeline).

## Why RAG is Well-Suited for This Use Case
- Scales well with unstructured logs: Your data is long, descriptive, and semi-structured—perfect for retrieval-based understanding.

- Retrieves only relevant context: Instead of analyzing all sensor logs, it fetches the most similar past examples.

- Works with long prompts: Embeddings + chunking let you handle large logs that would overflow token limits.

- Enables fault reasoning: Retrieved examples help the LLM infer patterns (e.g., "these readings often result in a fault").

# original LLM model vs LLM model with added context 
It directly told that, it is unfamiliar with specific event. The model with RAG pipeline got the context and try to give me the answer. Though the data is fully imbalanced. I will try to increase the k value or try to make the data balanced.
 
