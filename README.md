# RAG-Based Chatbot

This project implements a Retrieval Augmented Generation (RAG) based chatbot using LangChain, OpenAI, and ChromaDB, with a Gradio interface for easy interaction. The chatbot can answer questions based on a predefined knowledge base consisting of markdown files.

---

### Features

* **RAG Architecture:** Leverages LangChain to build a RAG pipeline for grounded responses.
* **Custom Knowledge Base:** Uses markdown files from a local directory as its knowledge source.
* **Vector Store:** Employs ChromaDB to store document embeddings for efficient retrieval.
* **OpenAI Integration:** Utilizes OpenAI's embeddings for document vectorization and `gpt-4o-mini` for conversational AI.
* **Gradio Interface:** Provides a user-friendly web interface for real-time chat.
* **Modular Design:** Components for data loading, chunking, embedding, vector store management, and chatbot logic are separated.

---

### Technologies Used

* Python 3.x
* [LangChain](https://www.langchain.com/)
* [OpenAI API](https://openai.com/docs/api/)
* [ChromaDB](https://www.trychroma.com/)
* [Gradio](https://www.gradio.app/)
* `python-dotenv`
* `numpy`
* `scikit-learn` (for TSNE visualization, although not directly used in the chat interface)
* `plotly` (for visualization, although not directly used in the chat interface)

---

### Installation

1.  **Clone the repository:**
    ```bash
    git clone <your-repository-url>
    cd <your-repository-name>
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate   # On Windows: `venv\Scripts\activate`
    ```

3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    (You will need to create a `requirements.txt` file based on the imports in `scratch_8.ipynb`. Key packages include `langchain`, `langchain-openai`, `langchain-chroma`, `gradio`, `python-dotenv`, `numpy`, `scikit-learn`, `plotly`).

    A sample `requirements.txt` might look like:
    ```
    langchain
    langchain-openai
    langchain-chroma
    gradio
    python-dotenv
    numpy
    scikit-learn
    plotly
    chromadb
    tiktoken
    ```

4.  **Set up OpenAI API Key:**
    Create a `.env` file in the root directory of your project and add your OpenAI API key:
    ```
    OPENAI_API_KEY="your_openai_api_key_here"
    ```

---

### Knowledge Base Setup

The chatbot relies on a local knowledge base.
1.  Create a directory structure similar to `files/knowledge-base/` in your project root.
2.  Inside `files/knowledge-base/`, create subdirectories (e.g., `products`, `contracts`, `company`, `employees`).
3.  Place your markdown (`.md`) knowledge base files within these subdirectories.

    Example structure:
    ```
    .
    ├── .env
    ├── scratch_8.ipynb
    ├── requirements.txt
    └── files/
        └── knowledge-base/
            ├── products/
            │   └── product_info.md
            ├── contracts/
            │   └── contract_details.md
            ├── company/
            │   └── about_us.md
            └── employees/
                └── employee_records.md
    ```

---

### Usage

1.  **Run the Jupyter Notebook:**
    Open the `scratch_8.ipynb` notebook and run all cells. This will:
    * Load your environment variables.
    * Load and chunk your markdown documents.
    * Create or update a ChromaDB vector store (`vector_db`).
    * Launch the Gradio chatbot interface.

    ```bash
    jupyter notebook scratch_8.ipynb
    ```

2.  **Interact with the Chatbot:**
    Once the Gradio interface launches, it will provide a local URL (e.g., `http://127.0.0.1:7865`). Open this URL in your web browser to start interacting with the RAG chatbot.

    The chatbot will retrieve relevant information from your knowledge base and use the `gpt-4o-mini` model to formulate answers.

---

### Configuration

* **`MODEL`**: The OpenAI model used for generating responses. Currently set to `'gpt-4o-mini'`. You can change this in the notebook.
* **`db_name`**: The name of the directory where the ChromaDB vector store will be persisted. Default is `'vector_db'`.

---

### Contributing

Feel free to fork the repository, open issues, and submit pull requests.


---

**Note:** The notebook includes code for visualizing the vector store using t-SNE and Plotly. While this is helpful for understanding the embeddings, it's not a core part of the chatbot's runtime functionality.
