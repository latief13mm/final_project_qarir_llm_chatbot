# Final project Qarir ganerator for LLM chatbot with pdf 

## Project Structure
```
ollama_pdf_rag/
├── src/                      # Source code
│   ├── app/                  # Streamlit application
│   │   ├── components/       # UI components
│   │   │   ├── chat.py      # Chat interface
│   │   │   ├── pdf_viewer.py # PDF display
│   │   │   └── sidebar.py   # Sidebar controls
│   │   └── main.py          # Main app
│   └── core/                 # Core functionality
│       ├── document.py       # Document processing
│       ├── embeddings.py     # Vector embeddings
│       ├── llm.py           # LLM setup
│       └── rag.py           # RAG pipeline
├── data/                     # Data storage
│   ├── pdfs/                # PDF storage
│   │   └── sample/          # Sample PDFs
│   └── vectors/             # Vector DB storage
├── notebooks/               # Jupyter notebooks
│   └── experiments/         # Experimental notebooks
├── tests/                   # Unit tests
├── docs/                    # Documentation
└── run.py                   # Application runner
```

### Prerequisites

1. **Install Ollama**
   - Visit [Ollama's website](https://ollama.ai) to download and install
   - Pull required models etc for this example:
     ```bash
     ollama pull llama3.2  # or your preferred model
     ollama pull nomic-embed-text
     ```

2. **Clone Repository**
   ```bash
   git clone https://github.com/latief13mm/final_project_qarir_llm_chatbot.git
   ```

3. **Set Up Environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: .\venv\Scripts\activate
   pip install -r requirements.txt
   ```

   Key dependencies and their versions:
   ```txt
   ollama==0.4.4
   streamlit==1.40.0
   pdfplumber==0.11.4
   langchain==0.1.20
   langchain-core==0.1.53
   langchain-ollama==0.0.2
   chromadb==0.4.22
   ```

### 🎮 Running the Application

#### Option 1: Streamlit Interface
```bash
python run.py
```
Then open your browser to `http://localhost:8501`

![Streamlit UI](st_app_ui.png)
*Streamlit interface showing PDF viewer and chat functionality*

#### Option 2: Jupyter Notebook
```bash
jupyter notebook
```
Open `updated_rag_notebook.ipynb` to experiment with the code

## 💡 Usage Tips

1. **Upload PDF**: Use the file uploader in the Streamlit interface or try the sample PDF
2. **Select Model**: Choose from your locally available Ollama models
3. **Ask Questions**: Start chatting with your PDF through the chat interface
4. **Adjust Display**: Use the zoom slider to adjust PDF visibility
5. **Clean Up**: Use the "Delete Collection" button when switching documents

## 🤝 Contributing

Feel free to:
- Open issues for bugs or suggestions
- Submit pull requests
- Comment on the YouTube video for questions
- Star the repository if you find it useful!

## ⚠️ Troubleshooting

- Ensure Ollama is running in the background
- Check that required models are downloaded
- Verify Python environment is activated
- For Windows users, ensure WSL2 is properly configured if using Ollama

### Common Errors

#### ONNX DLL Error
If you encounter this error:
```
DLL load failed while importing onnx_copy2py_export: a dynamic link Library (DLL) initialization routine failed.
```

Try these solutions:
1. Install Microsoft Visual C++ Redistributable:
   - Download and install both x64 and x86 versions from [Microsoft's official website](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist)
   - Restart your computer after installation

2. If the error persists, try installing ONNX Runtime manually:
   ```bash
   pip uninstall onnxruntime onnxruntime-gpu
   pip install onnxruntime
   ```

#### CPU-Only Systems
If you're running on a CPU-only system:

1. Ensure you have the CPU version of ONNX Runtime:
   ```bash
   pip uninstall onnxruntime-gpu  # Remove GPU version if installed
   pip install onnxruntime  # Install CPU-only version
   ```

2. You may need to modify the chunk size in the code to prevent memory issues:
   - Reduce `chunk_size` to 500-1000 if you experience memory problems
   - Increase `chunk_overlap` for better context preservation

Note: The application will run slower on CPU-only systems, but it will still work effectively.

## 🧪 Testing

### Running Tests
```bash
# Run all tests
python -m unittest discover tests

# Run tests verbosely
python -m unittest discover tests -v
```

### If you have any trouble
1. Use dependency with carnals venv to swich up it 
2. Check on file local_ollama_req.ipyn to check this out 
3. If still error fro running please run command this "chainlit run app.py -w --public"
4. And finally you can run this command to if still not running well command this "pip install --upgrade chainlit to running run.py
5. Enjoy for this app 





