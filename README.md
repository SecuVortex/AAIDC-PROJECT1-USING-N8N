# First RAG Agent Workflow 🚀

---

## Overview 🧠
This repository contains an n8n workflow that creates a simple but powerful Retrieval-Augmented Generation (RAG) agent using Google Gemini API. Upload your company documents (PDF, CSV) as a knowledge base, and chat with an AI assistant that answers questions based on your custom data.

---

## Features ✨
- 📄 Upload PDF or CSV files related to your business  
- 🤖 AI-powered chat using Google Gemini PaLM API  
- 🔍 Semantic search via in-memory vector embeddings  
- ⚙️ Easy setup with zero coding required using n8n  

---

## Demo 🎥




https://github.com/user-attachments/assets/904bc0f0-bcdf-4a85-840f-cffb692b588b



## Setup 🛠️
1. Import the `first-rag-agent.json` workflow into your n8n instance.  
2. Add your Google Gemini API credentials (`Google GeminiPaLM API account`).  
3. Activate the webhook URL in the "When chat message received" node.

---

## Uploading Your Data 📤
1. Execute the "Upload your file" node.  
2. Open the provided URL in your browser.  
3. Upload PDF or CSV files relevant to your company data.  
4. The workflow converts them into vector embeddings stored temporarily for fast semantic search.

---

## Using the Chat Assistant 💬
- Send your questions to the chat node's webhook URL.  
- The AI uses your uploaded data to provide accurate, context-aware answers.

---

## Limitations ⚠️
- Vector store is memory-based — data will be lost after restart.  
- Best for small datasets and experimentation.  
- Supports only PDF and CSV upload formats.

---

## Contributing 🤝
Enhancements and fixes are welcome! Fork the repo and submit pull requests.

---

## License 📄
MIT License. See LICENSE file for details.

---

Thank you for checking out this project! Feel free to ⭐ the repo if you find it useful.
