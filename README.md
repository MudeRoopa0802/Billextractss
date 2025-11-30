# Bajaj Health Datathon – Bill Data Extraction API

This project builds an API that extracts line-item details, subtotals, and the final total from medical bills and invoices. The API takes a document URL, downloads the bill, 
and processes it page by page to identify all valid bill items.

OCR is used to read the text from the bill. After extracting the raw text, the system detects table rows 
and extracts item name, item rate, item quantity, and item amount exactly as printed in the document. The pipeline removes duplicate entries, ignores summary rows like Total and Sub-total,
and avoids double counting. Every valid line item is captured to ensure nothing is missed. All item amounts are added to compute the final total, which is compared with the actual bill total for accuracy.

The output strictly follows the Postman collection schema and returns page-wise line items, the total item count, and token usage. The project includes preprocessing, 
OCR reading, rule-based table parsing, and total reconciliation logic to ensure clean and reliable results.

**Technology Stack:**  
Python, FastAPI/Flask for API, Tesseract/OCR Engine for text extraction, Regex and Pandas for parsing and cleaning, Uvicorn/Gunicorn for server deployment.

The solution exposes a single endpoint **POST /extract-bill-data**, which accepts a bill URL and returns the structured bill data in JSON format.
