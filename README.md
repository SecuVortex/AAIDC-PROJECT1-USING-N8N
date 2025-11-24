# First RAG Agent Workflow 🚀

> A comprehensive n8n workflow implementing Retrieval-Augmented Generation (RAG) with Google Gemini API for intelligent document-based conversations.

---

## 📋 Table of Contents
- [Overview](#overview-)
- [Architecture](#architecture-)
- [Features](#features-)
- [Demo](#demo-)
- [Prerequisites](#prerequisites-)
- [Installation & Setup](#installation--setup-)
- [Configuration](#configuration-)
- [Usage Guide](#usage-guide-)
- [RAG Implementation Details](#rag-implementation-details-)
- [Technical Resources](#technical-resources-)
- [Troubleshooting](#troubleshooting-)
- [Limitations](#limitations-)
- [Contributing](#contributing-)
- [License](#license-)

---

## Overview 🧠

This repository contains a production-ready n8n workflow that implements a sophisticated **Retrieval-Augmented Generation (RAG) agent** using Google Gemini API. The system enables organizations to create intelligent chatbots that can answer questions based on their proprietary documents, combining the power of large language models with domain-specific knowledge retrieval.

### Key Benefits
- **Zero-Code Implementation**: Built entirely with n8n's visual workflow editor
- **Enterprise-Ready**: Supports PDF and CSV document ingestion
- **Semantic Search**: Advanced vector embeddings for accurate information retrieval
- **Context Preservation**: Maintains conversation history for coherent interactions
- **Scalable Architecture**: Modular design for easy customization and extension

---

## Architecture 🏗️

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Document      │    │   Vector Store   │    │   Chat Interface│
│   Upload        │───▶│   (In-Memory)    │───▶│   (Webhook)     │
│   (PDF/CSV)     │    │   + Embeddings   │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         │                        │                        │
         ▼                        ▼                        ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Document      │    │   Semantic       │    │   Google Gemini │
│   Processing    │    │   Search         │    │   LLM           │
│   (Chunking)    │    │   (Retrieval)    │    │   (Generation)  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

---

## Features ✨

### Core Functionality
- 📄 **Multi-Format Support**: Upload PDF and CSV files
- 🤖 **AI-Powered Responses**: Google Gemini PaLM API integration
- 🔍 **Semantic Search**: Vector embeddings for precise information retrieval
- 💾 **Memory Management**: Conversation context preservation
- ⚙️ **No-Code Setup**: Complete visual workflow configuration

### Advanced Capabilities
- **Document Chunking**: Intelligent text segmentation for optimal retrieval
- **Vector Embeddings**: High-dimensional semantic representations
- **Context Window Management**: Efficient memory utilization
- **Webhook Integration**: RESTful API endpoints for chat interactions
- **Real-time Processing**: Instant document ingestion and query responses

---

## Demo 🎥

Experience the RAG agent in action with our comprehensive demo:

[![Watch Demo](https://img.youtube.com/vi/X-iej1SOwCY/0.jpg)](https://youtu.be/X-iej1SOwCY)

**🎬 Click the image above to watch the full walkthrough on YouTube!**

The demo covers:
- Complete setup process
- Document upload workflow
- Real-time chat interactions
- Performance optimization tips

---

## Prerequisites 📋

Before setting up the RAG agent, ensure you have:

### Required Software
- **Node.js** (v16.0.0 or higher)
- **n8n** (v1.0.0 or higher)
- **npm** or **yarn** package manager

### API Access
- **Google Gemini API Key** ([Get it here](https://makersuite.google.com/app/apikey))
- Active Google Cloud Platform account

### System Requirements
- **RAM**: Minimum 4GB (8GB recommended for large documents)
- **Storage**: 1GB free space
- **Network**: Stable internet connection for API calls

---

## Installation & Setup 🛠️

### Step 1: Install Dependencies

```bash
# Install n8n globally
npm install -g n8n

# Install required langchain nodes
npm install @n8n/n8n-nodes-langchain
```

### Step 2: Start n8n

```bash
# Start n8n server
n8n start

# Access n8n interface at http://localhost:5678
```

### Step 3: Import Workflow

1. Open n8n interface in your browser
2. Click **"Import from File"**
3. Select `first-rag-agent.json` from this repository
4. Click **"Import"** to load the workflow

### Step 4: Verify Installation

Check that all nodes are properly loaded:
- ✅ AI Agent
- ✅ Google Gemini Chat Model
- ✅ Vector Store (In-Memory)
- ✅ Document Loader
- ✅ Embeddings Generator

---

## Configuration ⚙️

### Google Gemini API Setup

1. **Obtain API Key**:
   - Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Create new API key
   - Copy the generated key

2. **Configure Credentials in n8n**:
   - Navigate to **Settings** → **Credentials**
   - Click **"Create New Credential"**
   - Select **"Google PaLM API"**
   - Enter your API key
   - Name it: `Google Gemini(PaLM) Api account`
   - Save the credential

3. **Apply Credentials to Nodes**:
   - **Google Gemini Chat Model** node
   - **Embeddings Google Gemini** node

### Webhook Configuration

1. **Chat Webhook**:
   - Open "When chat message received" node
   - Copy the webhook URL
   - Activate the webhook

2. **File Upload Webhook**:
   - Open "Upload your file here" node
   - Copy the form URL
   - Activate the webhook

---

## Usage Guide 📖

### Document Upload Process

1. **Access Upload Interface**:
   ```
   Execute the "Upload your file here" node
   Copy the generated form URL
   Open URL in browser
   ```

2. **Upload Documents**:
   - Select PDF or CSV files (max 10MB each)
   - Click "Submit" to process
   - Wait for confirmation message

3. **Verification**:
   - Check n8n execution log
   - Confirm vector embeddings creation
   - Validate document chunking

### Chat Interaction

1. **Send Messages**:
   ```bash
   # Using curl
   curl -X POST [WEBHOOK_URL] \
     -H "Content-Type: application/json" \
     -d '{"message": "What is the main topic of the uploaded document?"}'
   ```

2. **Expected Response Format**:
   ```json
   {
     "response": "Based on the uploaded document, the main topic is...",
     "sources": ["document_chunk_1", "document_chunk_2"],
     "confidence": 0.85
   }
   ```

---

## RAG Implementation Details 🔬

### Document Processing Pipeline

1. **Document Ingestion**:
   - File validation and format detection
   - Content extraction (PDF text, CSV parsing)
   - Metadata preservation

2. **Text Chunking Strategy**:
   - **Chunk Size**: 1000 characters
   - **Overlap**: 200 characters (20% overlap for context preservation)
   - **Splitting Method**: Sentence-aware segmentation

3. **Vector Embedding Generation**:
   - **Model**: Google Gemini Embeddings
   - **Dimensions**: 768
   - **Similarity Metric**: Cosine similarity

### Retrieval Mechanism

1. **Query Processing**:
   - User query embedding generation
   - Semantic similarity calculation
   - Top-k retrieval (k=5 by default)

2. **Context Assembly**:
   - Retrieved chunks ranking
   - Context window optimization
   - Relevance scoring

3. **Response Generation**:
   - Prompt engineering with retrieved context
   - Google Gemini LLM inference
   - Response post-processing

### Memory and Reasoning

- **Conversation Memory**: Buffer window (last 10 exchanges)
- **Context Preservation**: Maintains topic continuity
- **Reasoning Chain**: Multi-step logical inference
- **Hallucination Mitigation**: Source-grounded responses

---

## Technical Resources 📚

### Documentation Links
- [n8n Official Documentation](https://docs.n8n.io/)
- [Google Gemini API Guide](https://ai.google.dev/docs)
- [LangChain Integration](https://docs.langchain.com/docs/)
- [Vector Embeddings Explained](https://platform.openai.com/docs/guides/embeddings)

### Research Papers
- [RAG: Retrieval-Augmented Generation](https://arxiv.org/abs/2005.11401)
- [Dense Passage Retrieval](https://arxiv.org/abs/2004.04906)
- [In-Context Learning](https://arxiv.org/abs/2301.00234)

### Best Practices
- **Chunk Size Optimization**: Balance between context and specificity
- **Embedding Model Selection**: Consider domain-specific models
- **Retrieval Tuning**: Adjust similarity thresholds
- **Prompt Engineering**: Craft effective system prompts

---

## Troubleshooting 🔧

### Common Issues

**Issue**: "API Key Invalid"
```
Solution:
1. Verify API key format
2. Check credential configuration
3. Ensure API quotas are not exceeded
```

**Issue**: "Document Upload Failed"
```
Solution:
1. Check file size limits (max 10MB)
2. Verify supported formats (PDF, CSV)
3. Ensure webhook is activated
```

**Issue**: "Poor Response Quality"
```
Solution:
1. Improve document quality
2. Adjust chunk size parameters
3. Fine-tune retrieval settings
```

### Performance Optimization

- **Memory Usage**: Monitor vector store size
- **Response Time**: Optimize chunk retrieval count
- **API Costs**: Implement request caching
- **Accuracy**: Regular evaluation with test queries

---

## Limitations ⚠️

### Current Constraints
- **Storage**: In-memory vector store (data lost on restart)
- **Scalability**: Limited to small-medium datasets (<100MB)
- **Formats**: PDF and CSV only
- **Languages**: Optimized for English content
- **Concurrency**: Single-user sessions

### Planned Improvements
- Persistent vector storage integration
- Multi-format document support
- Batch processing capabilities
- Advanced chunking strategies
- Performance monitoring dashboard

---

## Contributing 🤝

We welcome contributions to improve the RAG agent workflow!

### How to Contribute
1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Development Guidelines
- Follow n8n workflow best practices
- Test with various document types
- Update documentation for new features
- Maintain backward compatibility

---

## License 📄

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### Third-Party Licenses
- n8n: [Fair-code License](https://github.com/n8n-io/n8n/blob/master/LICENSE.md)
- Google Gemini API: [Google Cloud Terms](https://cloud.google.com/terms)

---

## Acknowledgments 🙏

- **n8n Community** for the excellent workflow platform
- **Google AI** for the Gemini API access
- **LangChain** for RAG implementation patterns
- **Open Source Contributors** for continuous improvements

---

**⭐ Star this repository if you find it useful!**

**📧 Questions?** Open an issue or start a discussion.

**🚀 Ready to build your own RAG agent?** Follow the setup guide above!
