# First RAG Agent Workflow

## Overview
This repository contains an n8n workflow that sets up a simple Retrieval-Augmented Generation (RAG) agent using Google Gemini API. By uploading company documents (PDF or CSV), you create a custom knowledge base that the AI can reference to answer your queries.

## Features
- Upload PDF or CSV files as your knowledge base.
- AI chat powered by Google Gemini PaLM API.
- Vector-based semantic search using in-memory storage.
- Easy setup using n8n automation platform.

## Table of Contents
- [Setup](#setup)
- [Uploading Your Data](#uploading-your-data)
- [Using the Chat Assistant](#using-the-chat-assistant)
- [Limitations](#limitations)
- [Contributing](#contributing)
- [License](#license)

## Setup
1. Import the workflow JSON (`first-rag-agent.json`) into your n8n instance.
2. Enter your Google Gemini API credentials in the credentials section ("Google GeminiPaLM API account").
3. Activate the webhook URL from the "When chat message received" node to listen for chat messages.

## Uploading Your Data
1. Execute the "Upload your file" node.
2. Open the provided upload link in your browser.
3. Upload your company data files (PDF or CSV).
4. Files are converted into vector embeddings stored temporarily for semantic search.

## Using the Chat Assistant
- Interact with the AI by sending messages to the chat webhook URL.
- The AI will respond with answers based on your uploaded documents.

## Limitations
- Vector store is in-memory; restarting n8n clears all uploaded data.
- Suitable for test environments or small datasets.
- File uploads limited to PDF and CSV formats.

## Contributing
Contributions and improvements are welcome! Feel free to fork, submit issues, or open pull requests.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
