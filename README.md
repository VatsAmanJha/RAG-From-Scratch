### **RAG (Retrieval-Augmented Generation) System from Scratch**

This project demonstrates how to build a **Retrieval-Augmented Generation (RAG) system** entirely from scratch, without using any pre-existing frameworks such as Langchain or specialized tools for retrieval and generation. The system is designed to retrieve relevant document sections and generate answers to user queries using only base libraries and custom code.

### **Key Features**:

1. **Document Indexing and Chunking**:
   - The `indexing` function takes a large text document, splits it into smaller chunks of text (with an overlap to maintain context), and vectorizes them using **TF-IDF (Term Frequency-Inverse Document Frequency)**.
   - The vectorized chunks allow for easy retrieval based on user queries.

2. **Custom Retrieval Mechanism**:
   - The `retrieval` function implements a **cosine similarity** calculation to find the chunks most relevant to a given query. This step identifies which parts of the document contain information most closely matching the user’s input.
   - The process does not rely on any third-party retrieval libraries, purely using raw TF-IDF vectors and cosine similarity metrics to determine relevance.

3. **Text Generation Using LLM**:
   - The system integrates **Google's Gemini LLM** to generate responses. After retrieving the relevant document chunks, the system constructs a prompt, feeding both the user’s query and the retrieved content into the model for answer generation.
   - The generation step is entirely decoupled from external retrieval frameworks and built from scratch.

4. **RAG Chain Implementation**:
   - The `ragChain` function ties together retrieval and generation. It first finds the most relevant document chunks, then crafts a custom prompt for the LLM to generate a coherent and contextually relevant answer.
   - The prompt is designed to ensure that the LLM only uses factual information from the retrieved chunks, ensuring accurate responses.

### **How It Works**:
1. **Document Preparation**: The document is loaded and split into smaller, overlapping chunks to capture contextual information.
2. **Vectorization**: The chunks are converted into TF-IDF vectors for efficient similarity comparison.
3. **Retrieval**: Upon receiving a user query, the system calculates the cosine similarity between the query vector and document vectors, retrieving the most relevant chunks.
4. **Answer Generation**: Using the retrieved chunks, a prompt is created and passed to an LLM (Google Gemini) to generate an answer that directly addresses the user's question based on the retrieved content.

### **Technologies Used**:
- **NumPy**: For numerical computations.
- **Scikit-learn**: Using `TfidfVectorizer` for text vectorization and `cosine_similarity` for measuring similarities between the query and document chunks.
- **Google Generative AI (Gemini LLM)**: For generating natural language responses.
- **JSON**: For handling API keys and other configurations.

### **Key Advantages**:
- **No reliance on external frameworks**: Unlike systems that use Langchain or other pre-built solutions, this implementation is fully custom, providing maximum control over how retrieval and generation are handled.
- **Scalability**: The system can be extended to handle larger datasets, and the TF-IDF vectorization approach can be adjusted for more complex retrieval mechanisms.
- **Educational Value**: Building this RAG system from scratch helps in understanding the core mechanics of retrieval and generation, and it can be a foundation for more complex systems.

### **Use Cases**:
- **Document Search**: Ideal for querying large text documents and retrieving relevant sections.
- **Custom Knowledge-Based Q&A**: Can be adapted for knowledge systems in legal, academic, or technical fields.
- **Scalable Information Retrieval**: Suitable for building scalable systems where retrieval and generation must be highly customizable and efficient.

By implementing this RAG system from scratch, the project showcases the raw mechanics of retrieval-augmented generation, free from the abstraction layers and complexity of third-party frameworks, giving a deeper insight into how these systems work internally.