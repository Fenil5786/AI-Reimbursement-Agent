# 💰 AI Reimbursement Agent

An intelligent reimbursement processing system that automatically extracts expenses, validates them against company policies, and generates detailed reimbursement reports using AI and Retrieval-Augmented Generation (RAG).

## 🚀 Features

- **Intelligent Expense Extraction**: Automatically parse and structure expense information from user input
- **Policy-Based Validation**: Evaluate expenses against company reimbursement policies using LLM
- **RAG-Powered Policy Retrieval**: Fetch relevant policy snippets efficiently using semantic search
- **Automated Report Generation**: Create human-readable reimbursement reports with detailed verdicts
- **Streamlit UI**: User-friendly web interface for submission and tracking
- **LangGraph Orchestration**: Robust agentic workflow with clear node-based architecture

## 🏗️ Architecture

The system uses a **LangGraph-based workflow** with four main processing stages:

```
User Input 
    ↓
[ExtractExpenses] → Parse and structure expense data
    ↓
[RetrievePolicy] → Fetch relevant policy snippets via RAG
    ↓
[EvaluatePolicy] → Validate expenses against policy using LLM
    ↓
[GenerateReport] → Create final reimbursement report
    ↓
Report Output
```

### Core Components

- **State Management**: `ReimbursementState` TypedDict flows through all nodes
- **Policy Retrieval**: Vector store (Chroma) for semantic policy search
- **LLM Integration**: Groq API for cost-efficient policy evaluation
- **Embeddings**: Sentence Transformers for embedding generation

## 📋 Requirements

- Python 3.8+
- OpenAI or Groq API key
- Embeddings provider (default: Sentence Transformers)

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/ff.git
   cd ff
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Configure your `.env` file with:
   ```
   GROQ_MODEL=openai/gpt-oss-120b
   OPENAI_API_KEY=your_api_key_here
   GROQ_API_KEY=your_groq_api_key_here
   ```

## 💻 Usage

### Run the Streamlit Application

```bash
streamlit run app.py
```

The application will be available at `http://localhost:8501`

### Using the Application

1. **Input Expenses**: Submit expense descriptions in the web interface
2. **Upload Policy**: Provide your company reimbursement policy
3. **View Evaluation**: The system will:
   - Extract expense details
   - Retrieve relevant policy sections
   - Evaluate compliance
   - Generate a comprehensive report

## 📁 Project Structure

```
ff/
├── app.py                      # Streamlit UI entry point
├── requirements.txt            # Python dependencies
├── .env.example               # Environment variables template
├── src/
│   ├── __init__.py
│   ├── config.py              # LLM and configuration setup
│   ├── graph.py               # LangGraph workflow definition
│   ├── models/
│   │   ├── __init__.py
│   │   └── state.py           # ReimbursementState TypedDict
│   ├── nodes/
│   │   ├── __init__.py
│   │   ├── extract_expenses.py      # Expense extraction logic
│   │   ├── retrieve_policy.py       # RAG policy retrieval
│   │   ├── evaluate_policy.py       # Policy evaluation logic
│   │   └── generate_report.py       # Report generation
│   └── utils/
│       ├── __init__.py
│       ├── pdf_reader.py      # PDF parsing utilities
│       ├── json_parser.py     # JSON parsing utilities
│       └── rag.py             # RAG/vector store implementation
└── vectorstore/               # Chroma vector store data
    ├── chroma.sqlite3
    └── [collection directories]
```

## 🔧 Configuration

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `GROQ_MODEL` | Groq model identifier | `openai/gpt-oss-120b` |
| `OPENAI_API_KEY` | OpenAI API key for embeddings | (required) |
| `GROQ_API_KEY` | Groq API key for LLM | (required) |

### LLM Configuration

The default LLM is configured in `src/config.py` using Groq. To change:

1. Modify `get_llm()` in `src/config.py`
2. Update the model initialization with your preferred provider

## 🧪 Testing

Run tests using pytest:

```bash
pytest
```

## 📚 Technologies Used

- **LangChain**: LLM framework and utilities
- **LangGraph**: Agentic workflow orchestration
- **Streamlit**: Web UI framework
- **Chroma**: Vector database for embeddings
- **Groq API**: LLM provider
- **Sentence Transformers**: Embedding generation
- **PyPDF2**: PDF processing

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 💡 Future Enhancements

- [ ] Multi-currency support
- [ ] Approval workflow integration
- [ ] Integration with accounting systems
- [ ] Advanced expense categorization
- [ ] Batch processing capabilities
- [ ] Audit trail and compliance logging

## 📞 Support

For issues and questions, please open an issue on GitHub or contact the development team.

---

**Built with ❤️ using LangChain, LangGraph, and Streamlit**
