<div align="center">
  <a href="https://youtu.be/qAUiahzraFw">
    <img src="https://img.youtube.com/vi/qAUiahzraFw/0.jpg" alt="Indra OCR: Replace Google Tesseract & PaddleOCR on CPU">
  </a>
  <h3>📺 <a href="https://youtu.be/qAUiahzraFw">Watch the full tutorial on YouTube</a></h3>
</div>

# Indra OCR: Fast Document AI Engine

> **1.25M Parameters • 100% CPU Native • Zero GPU Required • 49 Pages/Sec Throughput**

An ultra-lightweight open-source document parsing engine by Datalab AI designed for maximum speed on standard CPU hardware. Indra OCR delivers complete page segmentation, line bounding boxes, reading order structuring, and table extraction with zero CUDA or PyTorch dependencies.

---

## ⚡ Key Highlights & Benchmark Showdown

- **Ultra-Small Footprint**: Only 1.25M parameters in the Latin recognizer (`rec.onnx`), 30MB ONNX network / 76MB bundle.
- **Pure CPU Scaling**: Scales from **212 ms per page** on 4 cores up to **49 pages per second** on 32 CPU cores.
- **Beats Heavy Pipelines**: Scores **71.4 on OmniParseBench** (with `--math`), outperforming Paddle PP-Structure (58.4) and Tesseract 5 (19.3) while running up to 15x faster.
- **Zero VRAM / Cloud Cost**: Runs 100% offline on consumer laptops and edge nodes with 0 MB GPU overhead.

| Engine / Pipeline | Headline | Text Score | Table Score | Layout Score | Latency / Page |
|---|---|---|---|---|---|
| **Indra OCR (Default Auto)** | **66.7** | 46.7 | 61.1 | **92.2** | **212 ms (15x Faster)** |
| **Indra OCR (--math)** | **71.4** | **62.7** | 59.6 | 92.0 | 357 ms |
| Paddle PP-StructureV3 | 58.4 | 55.6 | 47.8 | 71.7 | 40,958 ms (41s) |
| Paddle PP-OCRv6 (Text only) | – | 35.8 | 0.0 | – | 2,685 ms |
| Tesseract 5 (Latin model) | – | 19.3 | 0.0 | – | 5,496 ms (5.5s) |

---

## 🛠️ Quickstart Installation

```bash
# Install Indra OCR from PyPI
pip install indra-ocr

# Verify CLI installation
indra-ocr --help
```

---

## 🚀 Native CLI Usage

```bash
# Convert a single document directly to Markdown stdout
indra-ocr paper.pdf

# Batch convert an entire folder of PDFs into clean Markdown files
indra-ocr *.pdf --out results/

# Extract bounding boxes, line coordinates, and confidences into JSON
indra-ocr scan.png --format json

# Launch the local web inspector on http://localhost:8765
indra-ocr-viewer
```

---

## 🐍 Python SDK Integration

```python
import indra_ocr

# Initialize with multi-threading on CPU
conv = indra_ocr.load(threads=4)

# Convert single page or multi-page documents
for page in conv.convert("inputs/research_paper_table_page.png").pages:
    print(f"Source: {page.source} | Latency: {page.timings['total_ms']}ms")
    print(page.markdown)      # Structured Markdown tables & headings
    print(page.lines)         # Line bounding boxes, text & confidence
    print(page.blocks)        # Reading order layout segments
```

---

## 📂 Practical Use Cases

1. **High-Speed RAG Preprocessing**: Digest thousands of multi-page technical PDFs into clean knowledge-base Markdown without running costly GPU clusters.
2. **Automated Financial Ingestion**: Extract pixel bounding boxes and table structures from scanned multi-column invoices and balance sheets.
3. **Edge & Air-Gapped Deployment**: Run instant document AI in privacy-sensitive on-premise environments with 0MB VRAM requirements.

---

## 🔮 Future Feature Roadmap

- [ ] Integrated LaTeX equation synthesis directly in table cells.
- [ ] Automated multi-page layout stitching for spanning tabular grids.
- [ ] End-to-end continuous batch streaming for microservice containers.

---

<sub>Keywords: indra ocr, google tesseract, tesseract 5, tesseract ocr, tesseract replacement, paddleocr alternative, pp-structure, datalab ocr, datalab-to, cpu ocr, local ocr, tesseract alternative, tesseract vs ai, indra ocr tutorial, indra ocr review, indra ocr vs tesseract, google tesseract alternative, fastest cpu ocr, tesseract vs paddleocr, paddleocr comparison, ocr without gpu, ocr speed test, ocr accuracy test, pp-structurev3, pp-ocr alternative, local document ai, cpu document parsing, pytesseract alternative, easyocr alternative, doctr alternative, 1.25m vision model, indra ocr benchmark, datalab indra ocr, tesseract 5 replacement, offline cpu ocr, tesseract killer, indra ocr python, indra ocr install</sub>
