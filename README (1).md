# Sentence Transformers Chatbot & RAG Model

This repository contains a Python/Jupyter Notebook setup for a **Sentence Transformers & RAG Chatbot**. It utilizes state-of-the-art Hugging Face Transformer embeddings to perform semantic search, context retrieval, and AI-driven interactive conversation.

---

## 📌 Features

* **Semantic Search & Embeddings**: Uses `sentence-transformers` for dense vector representations and high-accuracy similarity matching.
* **Retrieval-Augmented Generation (RAG)**: Combines document retrieval with generative LLM responses.
* **Hugging Face Integration**: Downloads and caches pre-trained Hugging Face transformer models (`safetensors` format).
* **Interactive UI & Progress Tracking**: Integrated with Jupyter/Colab widgets (`ipywidgets`) for progress monitoring and dynamic updates.

---

## 🛠️ Requirements & Prerequisites

Ensure you have Python 3.8+ installed along with GPU support (recommended for faster model inference).

### Dependencies
Install the required dependencies using `pip`:

```bash
pip install sentence-transformers transformers torch datasets ipywidgets
```

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/sentence-transformer-chatbot.git
cd sentence-transformer-chatbot
```

### 2. Run the Notebook
Launch Jupyter Notebook or open the file in Google Colab:
```bash
jupyter notebook
```
Open `chatbot.ipynb` and run the cells sequentially.

---

## 📁 Repository Structure

```
.
├── chatbot.ipynb                   # Main Jupyter Notebook
├── config_sentence_transformers.json # Transformer configuration
├── sentence_bert_config.json        # SBERT model specifications
├── config.json                     # Primary model parameters
├── modules.json                    # Pipeline layout details
└── README.md                       # Project documentation
```

---

## ⚙️ How It Works

1. **Model Loading**: The script loads pre-trained Sentence Transformer weights (`model.safetensors`).
2. **Document Indexing**: Input text/documents are converted into embedding vectors and indexed for rapid similarity search.
3. **Query Processing**: When a user inputs a query, the system generates its vector embedding and retrieves the top-$K$ most relevant context chunks.
4. **Response Generation**: The retrieved context is passed to the chatbot pipeline to construct an accurate, context-aware response.

---

## 🤝 Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request if you'd like to improve model accuracy, add features, or refine performance.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
