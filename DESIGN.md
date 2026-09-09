1. **Risk Intelligence Tool - Stack:**



|Programming Language|Python|
|-|-|
|PDF Text Extraction with page-level information|PyMuPDF|
|Risk and mitigation extraction, classification, descriptions|OpenAI API|
|Structured and validated output|Pydantic|
|Simple Output Formats|CSV/JSON|
|Configuration and API-Key Management|dotenv|



**2. Parsing and Extraction:**



Annual Report --> PDF Parsing --> Risk Section Detection --> Page Aware Chunking --> LLM Extraction --> Validation --> Evaluation



a) PDF Parsing - Using PyMuPDF read each page, and retains/extracts text and page number.

b) Risk Section Detection - Instead of sending entire report to LLM, identifies pages that are relevant to risk disclosure. 

c) Section detection and creating chunks are deterministic, which reduced unnecessary LLM processing, reduces token limit by not passing entire report to LLM

c) LLM Extraction - It is responsible for semantic tasks such as, identifying risk, creating concise title, describing the risk, assigning category, identifying its mitigation, preserving supporting evidence

d) Validating page references and collecting evaluation metrics



**3. Work Decomposition:** 



Ingestion --> Section Detection --> Risk Extraction --> Validation --> Structured Output --> Evaluation



Each component has a single responsibility so that it can later be replaced or improved without redesigning the entire pipeline.



For example, the current section detector can eventually be replaced by a more sophisticated document-layout or retrieval approach without changing the downstream risk extraction contract.



**4. Trade-offs:**



1. Correctness over Maximum Coverage: Focused the first version on explicitly disclosing principal risks rather than attempting to infer every possible risk from the report. This reduces hallucination and makes the output easier for an analyst to trust.
2. Deterministic parsing + LLM semantics: Used python logic for page handling and document processing and use LLM for semantic understanding
3. Relevant Sections, not entire report: This reduces noise, cost and latency, since not passing all 195 pages to LLM
4. Simple Storage, not Database: JSON/CSV files for storage, not Database. But for production, move these results to persistent storage system and expose them through API



**5. Future Scaling Considerations:**



* Parallel processing of independent reports and chunks
* Caching extracted text and results
* For already used/unchanged docs, avoiding repeated LLM calls
* Will use smaller or cheaper models for classification/filtering
* Persistent storage for extracted reports and evaluation results
* Queue based processing for large report volumes and Batch processing during off-peak periods
* Monitoring token usage, processing time, failure rates and extraction quality



**6. Deferred Improvements:**



* Multi-company processing at production scale.
* Cross-company risk comparison.
* Year-over-year risk change detection.
* Interactive analyst UI.
* Real-time alerts.
* Enterprise authentication and access control.
* Advanced document-layout understanding.
* Production-grade distributed infrastructure.

