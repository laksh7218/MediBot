# Medi_MultiModal_RAG
A medical chatbot which not only utilises text from the datasource but also uses the tables and images to provide more contextually rich and accurate results.
### Evaluated several approaches for indexing images, text, and tables within our data source.

You can find the different methods in the 3 notebooks.

### 1.Multimodal_RAG
It is a Retrieval-Augmented Generation (RAG) pipeline that combines textual and visual modalities extracted from PDF documents. It generates multimodal embeddings, indexes them in a vector database, and uses them for context-aware question answering.

<img width="1822" height="518" alt="Screenshot 2025-07-28 at 4 39 52 AM" src="https://github.com/user-attachments/assets/8c345bdc-f2b4-40d6-9a01-f54bbdfbe737" />



---

## 🧠 Workflow Overview

MULTIMODEL_USED: "openai/clip-vit-base-patch32"

1. **PDF Data Loading**  
   A case report or academic paper is downloaded and loaded locally.

2. **Text, Tables and Image Extraction**  
   - Text is extracted from PDF using PyMuPDF.
   - Images (if any) are also extracted for embedding.
   - Table

3. **Embedding Generation**  

   - Generates embeddings for text using language models.
   - Optionally uses image encoders for visual content.

4. **Vector DB Creation**  
   - FAISS is used for indexing the embeddings.
   - Metadata is attached to each chunk for later retrieval.

5. **Querying via RAG**  
   - A user query is embedded.
   - Top-k relevant chunks are retrieved using vector similarity.
   - Retrieved context is used to generate a final response.

---

## 🛠️ Dependencies

Install required packages using:

```bash
pip install -r requirements_01.txt
```

------------------------


### 2.VLM_ColQwen2_RAG
VLM_ColQwen2_RAG is a multimodal retrieval-augmented generation (RAG) pipeline that uses the ColQwen2 vision-language model. It integrates image-based document processing (PDF-to-image), embedding-based retrieval, and answer generation. 


<img width="828" height="526" alt="Screenshot 2025-07-28 at 4 54 39 AM" src="https://github.com/user-attachments/assets/48a81324-7127-452e-8063-5687a7176bec" />
<img width="1460" height="829" alt="Screenshot 2025-07-28 at 4 55 39 AM" src="https://github.com/user-attachments/assets/4177f882-aa6b-468e-8c70-7718c2e894cf" />





---

## 🧠 Workflow Overview

MULTIMODEL_USED: "vidore/colqwen2-v0.1"

1. **PDF Data Loading**  
   A case report or academic paper is downloaded and loaded locally.

2. **Convert PDF to Images**  
   - PDFs are converted into images using PyMuPDF.
   - Each page becomes a separate image for inference.

3. **Embedding Generation**  

   - Images are passed through ColQwen2 to obtain embeddings.
   - Each embedding is indexed for later retrieval.

4. **Vector DB Creation**  
   - Qdrant is used for indexing the embeddings.
   - Metadata is attached to each chunk for later retrieval.

5. **Querying via RAG**  
   - A user query is embedded.
   - Top-k relevant chunks are retrieved using vector similarity.
   - Retrieved context is used to generate a final response.

---

## 🛠️ Dependencies

Install required packages using:

```bash
pip install -r requirements_02.txt
```

### 3.VLM_ColPali_RAG
Same as ColQWEN_RAG. Just test out for different VLM and also more number of datasource pdf files.

## 🛠️ Dependencies

Install required packages using:

```bash
pip install -r requirements_03.txt
```
