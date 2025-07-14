# 📦 RAG using ObjectBox Vector Store & LangChain with Groq LLaMA3

This project demonstrates how to build a **Retrieval-Augmented Generation (RAG)** chatbot using:

- ⚙️ **LangChain** for chaining and orchestration
- 🧠 **Groq's LLaMA3-8B-8192** via OpenAI-compatible endpoint
- 📚 **HuggingFace Embeddings** for semantic vector creation
- 🗃️ **ObjectBox** as a fast and lightweight embedded vector database
- 📄 **PDF-based document ingestion** via `PyPDFDirectoryLoader`
- 💻 **Streamlit** for interactive chat interface

---

## 🔧 What is ObjectBox?

[**ObjectBox**](https://objectbox.io/) is a high-performance embedded database optimized for edge and local applications. With vector search support, ObjectBox can be used as a vector store for fast and efficient semantic retrieval on local documents.

---

## 🚀 Features

- 📁 Load local PDFs and chunk them for retrieval
- ⚡ Perform semantic search with HuggingFace embeddings
- 📦 Store & retrieve vectors using **ObjectBox**
- 🤖 Generate responses using **Groq's LLaMA3-8B model**
- 🖥️ Simple, interactive **Streamlit-based** UI
- 🧪 Expandable section to explore retrieved chunks

---

## 📁 Directory Structure

```

.
├── app.py                    # Main Streamlit application
├── .env                      # Groq API key
├── census\_data/              # Folder with PDF documents
├── README.md

````

---

## 🛠️ Setup Instructions

### 1. Install Dependencies

```bash
pip install langchain langchain-community langchain-groq langchain-core streamlit python-dotenv sentence-transformers objectbox
````

> ⚠️ Make sure `objectbox` native bindings are properly installed based on your system. Refer to [ObjectBox Python Installation](https://github.com/objectbox/objectbox-python) if needed.

### 2. Environment Configuration

Create a `.env` file with:

```env
GROQ_API_KEY=your_groq_api_key
```

### 3. Add Your PDF Documents

Place your PDFs inside the `./census_data` directory.

---

## ▶️ Running the App

```bash
streamlit run app.py
```

* Click the **“Documents Embedding”** button to vectorize the documents.
* Ask any question related to the document content in the input box.

---

## 🧠 How It Works

### Step-by-step Flow:

1. **Document Loading:**

   * Loads PDFs using `PyPDFDirectoryLoader`.

2. **Chunking:**

   * Uses `RecursiveCharacterTextSplitter` (chunk size: 1000, overlap: 200).

3. **Embedding:**

   * Generates vector embeddings with HuggingFace's `all-MiniLM-L6-v2`.

4. **Vector Store:**

   * Stores the vectors using **ObjectBox** with `embedding_dimensions=768`.

5. **LLM Inference:**

   * Uses Groq’s `llama3-8b-8192` model via `ChatGroq`.

6. **RAG Pipeline:**

   * Combines retriever + document chain using `create_retrieval_chain`.

7. **UI:**

   * Built with Streamlit, including result + document context expansion.

---

## 💬 Sample Use Case

> **Input**: "What does the census say about urban population?"

> **Output**: A concise answer from the retrieved PDF content, along with the exact chunks used (shown in the expander).

---

## ✅ What You Learned

* ✅ How to use **ObjectBox** as a lightweight local vector database
* ✅ How to build an **RAG pipeline** with LangChain
* ✅ How to integrate **Groq’s LLaMA3** for inference
* ✅ How to ingest, split, and embed **PDF documents**
* ✅ How to build an interactive chatbot with **Streamlit**

---

## 🧩 Future Enhancements

* Save & persist ObjectBox vector store between sessions
* Enable multi-turn chat with LangChain memory
* Add file uploader to ingest PDFs dynamically
* Extend to use LangServe or FastAPI for API deployment

---

## 🙌 Credits

* [LangChain](https://www.langchain.com/)
* [Groq](https://console.groq.com/)
* [ObjectBox Vector Search](https://objectbox.io/vector-search/)
* [Hugging Face Embeddings](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)
* [Streamlit](https://streamlit.io/)

---

## 🚀 Local RAG with LLMs — Fast, Private, Production-Ready.
