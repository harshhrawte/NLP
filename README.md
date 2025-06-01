# NLP PDF Table Extractor

A Python-based tool that extracts and structures tabular data from PDF documents using Natural Language Processing techniques. This project automatically downloads PDFs from Google Drive, extracts text content, and intelligently identifies and formats tables into a well-structured JSON output 

## 🚀 Features

- **Google Drive Integration**: Direct PDF download from Google Drive links
- **Intelligent Text Extraction**: Uses PyMuPDF for accurate text extraction
- **Smart Table Detection**: Automatically identifies table structures in PDFs
- **Section Recognition**: Detects common section headers (SERVICES, MATERIALS, PRODUCTS, ITEMS)
- **Structured Output**: Converts extracted data into clean JSON format
- **Price Pattern Recognition**: Identifies and handles monetary values correctly
- **Flexible Row Handling**: Adapts to different table column structures

## 📋 Requirements

```
PyMuPDF (fitz)
gdown
re (built-in)
json (built-in)
os (built-in)
```

## 🛠️ Installation

1. Clone this repository:
```bash
git clone <your-repo-url>
cd nlp-pdf-extractor
```

2. Install required dependencies:
```bash
pip install PyMuPDF gdown
```

## 💻 Usage

### Basic Usage

Run the main script and provide a Google Drive link:

```bash
python pdf_extractor.py
```

When prompted, enter:
- Google Drive shareable link, or
- Direct Google Drive file ID

### Example Input
```
https://drive.google.com/drive/folders/1_xQe-Ict0TfXzpFYhRIB1fFFHtY19sVB?usp=drive_link
```

### Example Output Structure

```json
{
    "Pages": [
        {
            "Page_Number": 1,
            "Headers": ["Document Title", "Date", "Invoice #123"],
            "List_items": [
                {
                    "Description": "Professional Services",
                    "Quantity": "10",
                    "Unit Price": "$50.00",
                    "Total": "$500.00"
                },
                {
                    "Description": "Materials",
                    "Unit": "kg",
                    "Price": "$25.00"
                }
            ]
        }
    ]
}
```

## 🔧 Core Functions

### `extract_text_lines_from_pdf(pdf_path)`
Extracts all visible text lines from PDF pages using PyMuPDF.

### `group_table_rows(lines, section_keyword)`
Intelligently clusters text lines into table rows based on section headers and pattern recognition.

### `clean_and_format_table(table_rows)`
Converts raw table rows into structured dictionaries with appropriate column names.

### `is_price(value)`
Regex-based function to identify monetary values in various formats.

## 🎯 Supported Table Formats

- **5-column tables**: Description, Quantity, Unit Price, Total, Comments
- **4-column tables**: Description, Quantity, Unit Price, Total
- **3-column tables**: Description, Unit, Price
- **Flexible format**: Fallback for other structures

## 📊 Section Detection

The tool automatically detects and processes tables under these section headers:
- SERVICES
- MATERIALS  
- PRODUCTS
- ITEMS

## 🔍 Pattern Recognition

- **Price Detection**: `$1,234.56`, `1234.56`, `$1234`
- **Numbering**: Handles numbered lists (`1)`, `2)`, etc.)
- **Section Headers**: Identifies uppercase section titles
- **Table Boundaries**: Smart detection of table start/end points

## 📁 Output Files

- `extracted_data.json`: Structured JSON output with all extracted data
- Temporary `downloaded.pdf`: Automatically cleaned up after processing

## 🚦 Error Handling

- Invalid Google Drive link format detection
- File download error management
- PDF processing error handling
- Automatic cleanup of temporary files

## 🔮 Future Enhancements

- Support for multi-page table extraction
- Enhanced column header detection
- Integration with other cloud storage services
- GUI interface for easier usage
- Batch processing capabilities

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📞 Support

For questions or issues, please open an issue in the GitHub repository.

---

**Note**: This tool works best with PDFs containing structured tabular data. Results may vary depending on PDF formatting and layout complexity.
