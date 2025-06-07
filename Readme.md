# PDF/Image to Text Converter with Table Extraction

A comprehensive Python tool that converts PDFs and images to text with advanced table extraction, OCR, and AI enhancement using Groq models.

## ✨ Features

- **📄 PDF Text Extraction**: Extract regular text from PDFs
- **📊 Advanced Table Detection**: Multiple extraction methods (PyMuPDF, Tabula, Camelot)
- **🖼️ Image Processing**: Extract and process embedded images from PDFs
- **🔍 OCR with Table Detection**: Tesseract OCR optimized for tables in images
- **🤖 AI Enhancement**: Clean and format text using Groq models
- **📝 Multiple Formats**: Support for PDF, PNG, JPG, TIFF, and more

## 🚀 Quick Start

### Installation

```bash
# Core dependencies
pip install PyMuPDF Pillow pytesseract groq pandas

# Optional (recommended for better table extraction)
pip install tabula-py 'camelot-py[cv]'

# Install Tesseract OCR
# Windows: Download from GitHub releases
# macOS: brew install tesseract
# Linux: sudo apt-get install tesseract-ocr
```

### Basic Usage

```python
from pdf_converter import document_to_text_converter

# Convert PDF with all features
success = document_to_text_converter(
    input_path="document.pdf",
    output_path="extracted_text.txt",
    extract_tables=True,
    use_ocr=True,
    use_groq=True,
    groq_api_key="your_groq_api_key"
)
```

### Command Line

```bash
# Basic conversion
python pdf_converter.py document.pdf output.txt

# With all features enabled
python pdf_converter.py document.pdf output.txt --table-method all --use-groq --api-key your_key

# Process image with table detection
python pdf_converter.py screenshot.png text.txt --use-groq
```

## 📋 Configuration Options

| Parameter | Description | Default |
|-----------|-------------|---------|
| `extract_tables` | Extract tables from PDFs | `True` |
| `table_method` | Table extraction method (`pymupdf`, `tabula`, `camelot`, `all`) | `all` |
| `extract_images` | Extract images from PDFs | `True` |
| `use_ocr` | Perform OCR on images | `True` |
| `detect_tables_in_images` | Detect tables in images via OCR | `True` |
| `ocr_lang` | OCR language (`eng`, `spa`, `fra`, etc.) | `eng` |
| `use_groq` | Enhance text with Groq AI | `False` |

## 🛠️ Table Extraction Methods

- **PyMuPDF**: Fast, built-in table detection
- **Tabula**: Excellent for bordered tables
- **Camelot**: High-quality extraction with accuracy scores
- **All**: Use all methods for best results

## 📁 Output Structure

```
=== EXTRACTED TEXT FROM PDF ===
[Regular text content]

=== TABLES (PyMuPDF) ===
[Structured table data]

=== OCR TEXT FROM IMAGES ===
[Text from embedded images with table detection]
```

## 🔧 Environment Variables

Set your Groq API key:
```bash
export GROQ_API_KEY="your_groq_api_key_here"
```

## 📋 Supported Formats

- **Input**: PDF, PNG, JPG, JPEG, TIFF, BMP, GIF, WebP
- **Output**: Plain text with structured tables

## 🚨 Troubleshooting

**Tesseract not found?**
- Ensure Tesseract is installed and in your PATH
- Update the `tesseract_cmd` path in `setup_tesseract()` function

**Table extraction issues?**
- Try different `table_method` options
- For complex tables, use `camelot` method
- Enable Groq enhancement for better formatting

**OCR quality poor?**
- Ensure images are high resolution
- Try different OCR languages
- Use Groq enhancement to fix OCR errors

## 📄 License

MIT License - feel free to use and modify!
