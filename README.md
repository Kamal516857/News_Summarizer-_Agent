<p align="center">
  <img width="1264" height="842" alt="Image" src="https://github.com/user-attachments/assets/99552ded-4e38-44d9-ac1d-0ae89e30c5be" />
</p>

# 📰 News Summarizer Agent

![GitHub Repo stars](https://img.shields.io/github/stars/Kamal516857/News_Summarizer_Agent?style=social)
![GitHub forks](https://img.shields.io/github/forks/Kamal516857/News_Summarizer_Agent?style=social)
![GitHub issues](https://img.shields.io/github/issues/Kamal516857/News_Summarizer_Agent)
![Python Version](https://img.shields.io/badge/python-3.11+-blue)

**News Summarizer Agent** is a **Streamlit-based AI application** that allows you to ingest news articles from URLs, convert them into **vector embeddings**, and ask natural language questions to get **context-aware AI responses**.

It’s ideal for **analysts, journalists, and researchers** who want quick insights from multiple articles. 🚀

---

## ⚡ Features

* 🖊️ **Dynamic URL Input** – Add multiple article URLs via sidebar
* 🌐 **Automated Web Scraping** – Extracts content from given links
* ✂️ **Smart Text Chunking** – Splits large text for better processing
* ⚡ **Semantic Search** – Fast retrieval using **FAISS vector store**
* 🧠 **AI-Powered Answers** – Uses **LLaMA 3.3 70B (via ChatGroq)**
* 💾 **Persistent Storage** – Save & reload embeddings
* 🐞 **Debug Mode** – Inspect retrieved chunks
* 🎨 **User-Friendly UI** – Clean Streamlit interface

---

## 📊 Workflow

```mermaid
flowchart LR
    A[User Inputs URLs] --> B[Load Articles]
    B --> C[Split into Chunks]
    C --> D[Generate Embeddings]
    D --> E[Store in FAISS]
    E --> F[User Query]
    F --> G[Retrieve Relevant Data]
    G --> H[LLM Processing]
    H --> I[Display Answer]
```

---

## 🛠️ Tech Stack

* **Python 3.11+**
* **Streamlit** – UI Framework
* **LangChain** – LLM workflows & pipelines
* **FAISS** – Vector similarity search
* **HuggingFace Transformers** – Embeddings
* **ChatGroq (LLaMA 3.3 70B)** – LLM
* **dotenv** – Environment management
* **pickle** – Storage

---

## 🚀 Getting Started

### 1️⃣ Clone Repository

```bash
git clone https://github.com/Kamal516857/News_Summarizer_Agent.git
cd News_Summarizer_Agent
```

### 2️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Setup Environment Variables

Create a `.env` file:

```env
GROQ_API_KEY=your_api_key_here
```

### 4️⃣ Run the App

```bash
streamlit run app.py
```

Open in browser:
👉 [http://localhost:8501](http://localhost:8501)

---

## 📝 Usage

1. Enter **1–10 news URLs** in the sidebar
2. Click **"Process URLs"**
3. Ask your question in the input box
4. View **AI-generated answers + retrieved context**

---

## 🔧 Code Highlights

### Vector Store Creation

```python
vectorstore = FAISS.from_documents(docs, embeddings)
with open("faiss_store.pkl", "wb") as f:
    pickle.dump(vectorstore, f)
```

### LLM Q&A Chain

```python
chain = (
    {
        "context": RunnablePassthrough(lambda _: "\n\n".join(doc.page_content for doc in docs)),
        "question": RunnablePassthrough(),
    }
    | prompt
    | llm
    | StrOutputParser()
)

result = chain.invoke(query)
```


#### You can access the website via **"https://news-summarizer-agent.streamlit.app/"**
