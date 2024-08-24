

---

## PDF Question Answering App

This project is a **Streamlit-based** web application that allows users to upload a PDF document and ask questions about its content. The app uses a combination of **Hugging Face transformers** and **LangChain** libraries to process the PDF, create embeddings, and build a conversational retrieval-based QA chain that interacts with the user in real-time.

### Key Features

- **PDF Document Upload**: Users can upload a PDF file directly through the Streamlit interface.
- **Text Processing and Embedding Creation**: The application processes the uploaded PDF by splitting it into smaller text chunks and generating embeddings using the `sentence-transformers/all-mpnet-base-v2` model.
- **Conversational QA Chain**: The app sets up a conversational retrieval chain using the processed text data, allowing users to ask questions about the PDF content.
- **Efficient Query Handling**: The app is optimized to handle queries efficiently, running on a quantized large language model (`meta-llama/Llama-2-7b-chat-hf`), with the ability to stop text generation once a satisfactory answer is generated.

### How It Works

1. **Document Loading**: Once a PDF file is uploaded, it is loaded using `PyPDFLoader`, which reads the file and extracts the text content.

2. **Text Splitting**: The extracted text is split into manageable chunks using `RecursiveCharacterTextSplitter`, which ensures the chunks are neither too small nor too large, preserving the context for better embeddings.

3. **Embedding Generation**: The text chunks are embedded using a pre-trained transformer model (`sentence-transformers/all-mpnet-base-v2`), which converts the text into numerical representations.

4. **Vector Store Creation**: The embeddings are stored in a FAISS vector store, which allows for fast and efficient retrieval during query processing.

5. **Model Setup**: The application uses the `meta-llama/Llama-2-7b-chat-hf` model, which is optimized with 4-bit quantization to run on GPUs with limited memory. The model is initialized with custom stopping criteria to avoid generating unnecessary text.

6. **Conversational QA Chain**: A conversational retrieval QA chain is set up using LangChain, which retrieves relevant text chunks from the vector store based on the user’s query and generates an answer using the language model.

7. **Interactive Querying**: Users can input their questions about the PDF through the Streamlit interface. The app processes these queries in real-time and returns concise answers based on the document content.

### How to Run

1. **Prerequisites**: Ensure you have Python and the required libraries installed. You also need a Hugging Face access token for downloading models.

2. **Running the App**: The app is set up to run in a Streamlit environment. The local server is exposed using `localtunnel` for easy access from any device.

3. **Accessing the App**: Once the Streamlit server is running, you will receive a URL to access the app in your browser. Follow the on-screen instructions to interact with the PDF.

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/pdf-qa-app.git
   cd pdf-qa-app
   ```

2. Install the required packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Run the Streamlit app:

   ```bash
   streamlit run app.py
   ```

4. Expose the app using localtunnel (or another tunneling service):

   ```bash
   npx localtunnel --port 8501
   ```

---

