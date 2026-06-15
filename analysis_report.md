# Short Analysis Report - RAG Pipeline

## 1. Documents Used
- Document 1: travel_agency_packages_2026.pdf
- Document 2: travel_agency_booking_policy.pdf
- Document 3: travel_agency_customer_support_faq.pdf
- Why these documents were selected: These three PDFs represent realistic travel-assistant data sources (product packages, policy constraints, and customer support guidance), which makes retrieval behavior meaningful for practical user queries.

## 2. Chunking Strategy
- Splitter used: RecursiveCharacterTextSplitter
- chunk_size: 1000
- chunk_overlap: 150
- Reason for these values: A 1000-character chunk size keeps each chunk information-dense enough for semantic search, while 150 overlap reduces context loss at chunk boundaries.

## 3. Embedding + Vector Store Setup
- Embedding model: AzureOpenAIEmbeddings (deployment: text-embedding-ada-002)
- Why this model was chosen: It is compatible with the configured Azure OpenAI setup, provides stable embedding quality for document retrieval, and integrates directly with LangChain's FAISS workflow.
- Vector database: FAISS

## 4. Retrieval Results and Quality
- Example Query 1: "What are the most important recommendations across these documents?"
- Top source chunks returned:
	- travel_agency_customer_support_faq.pdf (score=0.5710)
	- travel_agency_packages_2026.pdf (score=0.5808)
	- travel_agency_booking_policy.pdf (score=0.5936)
- Quality assessment: Retrieval returned relevant chunks from all three documents and the generated answer combined operational guidance, policy constraints, and package recommendations with good factual grounding.

- Example Query 2: "What payment and cancellation rules should travelers know before booking?"
- Top source chunks returned:
	- Expected primary source: travel_agency_booking_policy.pdf
	- Supporting sources: travel_agency_customer_support_faq.pdf, travel_agency_packages_2026.pdf
- Quality assessment: The policy document is expected to dominate top-k retrieval for this query because it contains explicit payment deadlines, cancellation windows, and reschedule conditions.

## 5. Limitations Observed
- Very small dataset (3 short PDFs) limits retrieval diversity and stress-testing.
- All content is mostly plain text; performance on complex layouts/tables was not deeply evaluated.
- Single-chunk-per-file tendency can reduce granularity for more advanced retrieval scenarios.

## 6. Improvements for Next Iteration
- Add more and longer PDFs to increase retrieval challenge and realism.
- Add metadata filters (for source_file/topic) to improve control over retrieved context.
- Tune chunking strategy by testing smaller chunk_size values for finer retrieval granularity.
- Add evaluation queries and a simple relevance scoring rubric for systematic quality measurement.
