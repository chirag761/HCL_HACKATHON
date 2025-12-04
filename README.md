# HCL_HACKATHON
How the RAG Flow Works

Upload a document

Text is extracted from the document

The text is split into chunks so the model can process it

Each chunk is turned into an embedding

Embeddings are stored in Chroma vector database

You ask a question

The system finds the most relevant chunks

The LLM uses only those chunks to generate an answer

You receive an answer with supporting context

FlowChart:

                     ┌────────────────────────┐
                     │      User Question      │
                     └────────────┬───────────┘
                                  │
                                  ▼
                    ┌──────────────────────────┐
                    │ Convert Question into     │
                    │ Embedding (Vector)        │
                    │ using Embedding Model     │
                    └────────────┬─────────────┘
                                  │
                                  ▼
                 ┌──────────────────────────────────┐
                 │ Search Similar Chunks in Vector  │
                 │ Database (Chroma / FAISS / etc.) │
                 └───────────────┬──────────────────┘
                                 │
             Retrieved Top-K     ▼
       ┌─────────────────────────────────────┐
       │     Return Relevant Document         │
       │     Chunks (context passages)        │
       └─────────────────────┬───────────────┘
                             │
                             ▼
           ┌─────────────────────────────────────┐
           │ Build Prompt for LLM:               │
           │  - User question                    │
           │  - Retrieved document chunks        │
           │  - System instructions              │
           └──────────────────────┬──────────────┘
                                  │
                                  ▼
                ┌────────────────────────────────┐
                │   LLM Generates Final Answer    │
                │     (GPT-4 / GPT-3.5 / Mistral) │
                └───────────────────┬────────────┘
                                    │
                                    ▼
                        ┌─────────────────────┐
                        │ Return Answer to     │
                        │      the User        │
                        └─────────────────────┘


Why RAG is Useful:

It gives accurate answers based on your own documents

It avoids hallucinations by limiting the model to real content

It allows long documents to be processed effectively

It’s great for summaries, Q&A, and extracting information
