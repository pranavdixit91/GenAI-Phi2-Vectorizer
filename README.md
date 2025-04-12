# Phi2 Vectorizer

The **Phi2 Vectorizer** is a Python-based tool for processing and vectorizing documents using the LangChain library. It loads documents from a specified directory, splits them into manageable chunks, and creates a FAISS vector store for efficient similarity search and retrieval.

## Features

- **Document Loading**: Supports loading `.txt`, `.md`, and `.html` files from a directory.
- **Text Splitting**: Splits documents into smaller chunks for better vectorization.
- **Vectorization**: Uses HuggingFace embeddings (`all-MiniLM-L6-v2`) for creating vector representations of text.
- **FAISS Vector Store**: Stores the vectorized chunks in a FAISS database for efficient similarity search.
- **Customizable**: Easily configurable for different models, chunk sizes, and file types.

## Project Structure

```
phi2-vectorizer/
├── app/
│   ├── vectorizer.py       # Main script for vectorizing documents
├── docs/                   # Directory containing input documents (to be created by the user)
├── my_vector_db/           # Directory where the FAISS vector store will be saved
├── requirements.txt        # Python dependencies for the project
└── README.md               # Project documentation
```

## Prerequisites

- Python 3.8 or higher
- A working internet connection (for downloading models and dependencies)

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd phi2-vectorizer
   ```

2. Create and activate a virtual environment:
   ```bash
   # On Windows
   python -m venv venv
   .\venv\Scripts\activate
   ```

3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Place your documents in the `docs/` directory. Supported file formats include `.txt`, `.md`, and `.html`.

2. Run the `vectorizer.py` script:
   ```bash
   python app/vectorizer.py
   ```

3. The script will:
   - Load documents from the `docs/` directory.
   - Split the documents into chunks.
   - Vectorize the chunks using HuggingFace embeddings.
   - Save the FAISS vector store in the `my_vector_db/` directory.

4. Once complete, you will see the following output:
   ```
   <number> documents loaded
   <number> chunks created
   Vectorizing chunks...
   Vectorization complete!
   Vector DB created successfully!
   ```

## Configuration

You can customize the following parameters in `vectorizer.py`:

- **Chunk Size and Overlap**:
  ```python
  splitter = RecursiveCharacterTextSplitter(chunk_size=500, chunk_overlap=50)
  ```
  Adjust `chunk_size` and `chunk_overlap` to control the size and overlap of text chunks.

- **Embedding Model**:
  ```python
  embeddings = HuggingFaceEmbeddings(model_name="all-MiniLM-L6-v2")
  ```
  Replace `"all-MiniLM-L6-v2"` with any other HuggingFace model name.

- **Input and Output Paths**:
  Modify the `docs_path` and `my_vector_db_path` variables to change the input and output directories.

## Dependencies

The project uses the following Python libraries:

- `langchain`: For document processing and vectorization.
- `sentence-transformers`: For HuggingFace embeddings.
- `faiss-cpu`: For creating and managing the FAISS vector store.
- `unstructured`: For loading and parsing documents.
- `pypdf`: For handling PDF files (if needed).
- `markdown`: For processing Markdown files.
- `gradio`: For building interactive UIs (optional).

Refer to `requirements.txt` for the full list of dependencies.

## Troubleshooting

- **ModuleNotFoundError**: Ensure all dependencies are installed by running:
  ```bash
  pip install -r requirements.txt
  ```

- **Path Issues**: Verify that the `docs/` directory exists and contains the input files. Ensure the script is executed from the project root directory.


## Acknowledgments

- [LangChain](https://github.com/hwchase17/langchain) for providing the framework for document processing and vectorization.
- [HuggingFace](https://huggingface.co/) for pre-trained embedding models.
- [FAISS](https://github.com/facebookresearch/faiss) for efficient similarity search.

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests to improve the project.

---
Happy vectorizing!