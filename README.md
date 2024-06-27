# llm-chatbot-llama2-langchain

# Objective
I am using Llama2, langchain and ChromaDB to create a retirival augmented generation (RAG) which allows to ask question about artificial intelligence etc. At first retrival step is done to find the relevant documents stored in the vector database where they are indexed.
LLM - Large Language Model
Llama 2.0 - LLM from Meta
Langchain - a framework designed to simplify the creation of applications using LLMs
Vector database - a database that organizes data through high-dimmensional vectors
ChromaDB - vector database
RAG - Retrieval Augmented Generation (see below more details about RAGs) 
LlaMA 2 model is pretrained and fine-tuned with 2 Trillion tokens and 7 to 70 Billion parameters which makes it one of the powerful open source models
# What is RAG
Large Language Models (LLMs) has proven their ability to understand context and provide accurate answers to various NLP tasks, including summarization, Q&A, when prompted. While being able to provide very good answers to questions about information that they were trained with, they tend to hallucinate when the topic is about information that they do "not know", i.e. was not included in their training data. Retrieval Augmented Generation combines external resources with LLMs. The main two components of a RAG are therefore a retriever and a generator.

The retriever part can be described as a system that is able to encode our data so that can be easily retrieved the relevant parts of it upon queriying it. The encoding is done using text embeddings, i.e. a model trained to create a vector representation of the information. The best option for implementing a retriever is a vector database. As vector database, there are multiple options, both open source or commercial products. Few examples are ChromaDB, Mevius, FAISS, Pinecone, Weaviate. Our option in this Notebook will be a local instance of ChromaDB (persistent).

For the generator part, the obvious option is a LLM. In this github we will use a LLaMA v2 model from Meta

# Flow of the code
1. Import all the important libraries for loading the dataset, chunks creator, retrival and storing vectors
2. Define, import and prepare the model.
3. Tokenize the texts from datasets
4. Funcion for creating chunks from the documents, embeddings and insertion of chunks to the vector databases
5. Function for retrieving the result from the vector DB, implementing LLM for the text generation over retrieved results
6. Instead of directly using query to get the documents from vector DB, firstly we will pass our query to LLM to get a hypothetical answer from the LLM
7. We will combine that hypothetical answer with our query to get an accurate and closely related answers/documents from the vector database
8. We will be using advanced RAG like cross-encoder to score the retrieval of the documents according to the query that we have set


