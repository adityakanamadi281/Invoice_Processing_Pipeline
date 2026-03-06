# Invoice Data Extraction Pipeline

## Overview

This project extracts structured data from **multiple PDF invoices** and converts them into machine-readable formats such as **JSON and CSV**.

The pipeline automatically:

1. Downloads invoice PDFs from Google Drive
2. Extracts text from each invoice
3. Parses key invoice fields using pattern matching
4. Extracts line-item details
5. Converts the data into structured formats (JSON / CSV)
6. Loads the data into Pandas DataFrames for analysis

This project demonstrates a **document processing pipeline commonly used in financial automation, accounting systems, and AI document intelligence applications.**

---

# Project Workflow

```
PDF Invoices
     │
     ▼
Download from Google Drive
     │
     ▼
Text Extraction (pdfplumber)
     │
     ▼
Regex-based Field Extraction
     │
     ▼
Line Item Parsing
     │
     ▼
Structured Invoice Object
     │
     ▼
Export to JSON / CSV
     │
     ▼
Data Analysis with Pandas
```

---

# Features

* Automated **bulk invoice processing**
* Extracts important invoice fields:

  * Invoice Number
  * Invoice Date
  * Vendor Name
  * Customer ID
  * Shipping Address
  * Order Date
  * Invoice Total

* Extracts **line item data**

  * Description
  * Quantity
  * Unit Price
  * Line Total

* Converts results into:

  * `JSON`
  * `CSV`
  * `Pandas DataFrames`

---

# Technologies Used

| Technology | Purpose |
|----------|----------|
| Python | Core programming language |
| pdfplumber | PDF text extraction |
| regex | Field extraction from text |
| pandas | Data manipulation |
| pydantic | Data validation |
| gdown | Download files from Google Drive |
| csv / json | Export structured data |

---

# Project Structure

```
.
├── Multiple_Invoices_.ipynb
├── invoices/                # Downloaded PDF invoices
├── invoices_output.json     # Structured invoice output
├── invoices.csv             # Invoice summary table
├── lineitems.csv            # Line item table
└── README.md
```

---

# Installation

Install required dependencies:

```bash
pip install pdfplumber pandas pydantic gdown
```

Optional dependencies used in the notebook:

```bash
pip install easyocr pdf2image pypdf
apt-get install poppler-utils
```

---

# Usage

### 1 Download Invoice PDFs

Update the Google Drive link:

```python
drive_url = "YOUR_GOOGLE_DRIVE_LINK"
```

The script downloads invoices into:

```
/invoices
```

---

### 2 Extract Text from PDFs

The pipeline reads each invoice and extracts raw text using:

```python
extract_text_from_pdf()
```

This function processes every page of the invoice.

---

### 3 Extract Invoice Fields

Key invoice information is extracted using **regular expressions**:

```python
extract_invoice_fields(text)
```

Fields include:

* Invoice Date
* Invoice Number
* Customer ID
* Invoice Total

---

### 4 Extract Line Items

Line items such as product description and prices are extracted using:

```python
extract_items(text)
```

Each item includes:

```
description
quantity
unit_price
line_total
```

---

### 5 Convert Data to JSON

All extracted invoices are saved as structured JSON:

```python
invoices_output.json
```

Example:

```json
{
  "Invoice_Number": "12345",
  "Invoice_Date": "01/10/2024",
  "Vendor_Name": "ABC Supplies",
  "Invoice_Total": 1200.50
}
```

---

### 6 Convert Data to CSV

Two CSV files are generated.

#### Invoice Table

```
invoices.csv
```

| Invoice_Number | Vendor_Name | Invoice_Date | Invoice_Total |
|---------------|-------------|--------------|--------------|

#### Line Item Table

```
lineitems.csv
```

| Invoice_Number | description | quantity | unit_price | line_total |
|---------------|-------------|----------|-----------|-----------|

---

### 7 Load Data for Analysis

```python
import pandas as pd

invoices = pd.read_csv("invoices.csv")
lineItems = pd.read_csv("lineitems.csv")
```

Now the data can be used for:

* financial analysis
* dashboards
* AI systems
* accounting automation

---

# Example Use Cases

This pipeline can be used for:

* **AI Accounting Copilot**
* **Financial document processing**
* **Accounts payable automation**
* **Invoice analytics dashboards**
* **RAG systems for financial documents**

---

# Future Improvements

Possible enhancements:

* OCR support for scanned invoices
* LLM-based invoice understanding
* Automatic vendor detection
* Fraud detection system
* Real-time invoice ingestion pipeline
* Integration with accounting software (QuickBooks, SAP)

---

# Author

Aditya Kanamadi  

---

# License

This project is open-source and available under the MIT License.
