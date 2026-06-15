# RAG Pipeline for Travel Documents

## Project Summary
This project implements a Retrieval-Augmented Generation (RAG) workflow that turns PDF travel documents into a searchable knowledge base. The pipeline ingests documents, splits them into chunks, converts chunks to embeddings, stores vectors in FAISS, and retrieves the most relevant context for user questions before generating grounded answers.

## Project Description (Reworded)
The goal is to build a practical AI document assistant using real-world files instead of toy examples. In this implementation, multiple PDFs are processed and indexed so semantic search can find the best-matching content for a query. The retrieved text is then used by an LLM to produce answers that stay tied to source material.

Core workflow:
1. Load 2-3 PDF files (manuals, reports, or policy-style documents).
2. Chunk the extracted text for retrieval.
3. Generate embeddings using OpenAI/Azure OpenAI models.
4. Store and query embeddings with a FAISS vector database.
5. Retrieve top relevant chunks for each user question.
6. Generate a context-aware response from retrieved evidence.

## Tools and Stack
- Visual Studio Code
- Python
- LangChain
- FAISS
- OpenAI API / Azure OpenAI

## Dataset Used in This Repo
- pdfs/travel_agency_packages_2026.pdf
- pdfs/travel_agency_booking_policy.pdf
- pdfs/travel_agency_customer_support_faq.pdf

## Deliverables Included
- main.ipynb: completed notebook pipeline
- outputs/sample_output.txt: sample retrieval and answer output
- analysis_report.md: short analysis report
- pdfs/: sample source PDFs used for indexing

## Submission Notes
For LMS submission, zip the project folder with the notebook, sample outputs, source PDFs, and analysis report.
