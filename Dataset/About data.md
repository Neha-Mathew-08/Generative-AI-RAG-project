Data Description
1. Source and Type

The project uses employee handbook PDFs from multiple companies.

Examples include:

US_Employee_Handbook.pdf – typical HR policies for a US-based company.

handbook-dataset.pdf – another company’s employee handbook with different policies.

These handbooks are unstructured documents containing information about leave policies, probation periods, remote work, benefits, and company rules.

2. Why This Data is Relevant

HR handbooks are the primary authoritative source for company policies.

By using them as the data source, the RAG system can:

Provide accurate and company-specific answers.

Avoid relying on generic HR knowledge or public LLM data.

Scale to multiple companies without manual curation.

3. Data Processing

PDF extraction: Used pdfplumber to extract text from PDFs while preserving paragraphs and sections.

Chunking: Long documents were split into 400–800 word chunks with overlaps of 50–100 words to maintain context.

Embedding: Each chunk is converted to a vector embedding using BAAI/bge-small-en-v1.5.

Vector indexing: Chunks are stored in a FAISS index for fast semantic retrieval during queries.

4. Data Considerations

Multi-company support: Each chunk is labeled with its company to prevent mixing policies from different organizations.

Quality control: Chunking and embeddings ensure that queries retrieve relevant and accurate information.

Scalability: New employee handbooks can be added by following the same ingestion and embedding pipeline.
