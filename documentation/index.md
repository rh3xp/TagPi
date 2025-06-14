# 📁 TagPi: AI-Powered Folder Organizer on Raspberry Pi 4 (4GB RAM)

This documentation walks through building **TagPi**, a lightweight open-source LLM-powered folder organization tool on a Raspberry Pi 4 (4GB RAM). It supports multilingual filenames (like Hindi) and outputs a new structured directory based on tags inferred from filenames.

---

## 📚 Overview

### ✅ Objectives:

1. Install an open-source LLM compatible with Raspberry Pi 4.
2. Recursively read an unstructured folder with multilingual filenames.
3. Save metadata (name, path, type, size, etc.) to a CSV file.
4. Use LLM to infer tags/topics based on filenames and classify files.
5. Generate a static HTML view of the new structure.
6. Move files using Python's `os` and `shutil`, avoiding filename conflicts.

### 📂 Target File Types

* `.pdf`, `.docx`, `.jpg`, `.png`, `.txt`, `.xlsx`, etc.

### 🔧 Tools Used

* **LLM:** [TinyLLM](https://github.com/mckaywrigley/tinyllm) (or distilled models from HuggingFace)
* **Lang Support:** UTF-8 + `langdetect`
* **HTML Renderer:** Jinja2
* **Python Libraries:** `os`, `shutil`, `pandas`, `langdetect`, `jinja2`, `transformers`

---

## 🧩 Modular File Structure

```bash
tagpi/
├── README.md
├── index.md
├── 1_setup_llm.md
├── 2_scan_directory.md
├── 3_tag_files.md
├── 4_generate_html.md
├── 5_move_files.md
├── scripts/
│   ├── scan_directory.py
│   ├── tag_generator.py
│   ├── html_generator.py
│   ├── file_mover.py
│   └── utils.py
├── data/
│   └── file_index.csv
├── templates/
│   └── structure_template.html
└── output/
    └── final_structure.html
```

---

## 🔗 Linked Documentation

* [Step 1: Setup Lightweight LLM](1_setup_llm.md)
* [Step 2: Scan and Log Folder Structure](2_scan_directory.md)
* [Step 3: Generate Tags and Labels](3_tag_files.md)
* [Step 4: Render Static HTML Page](4_generate_html.md)
* [Step 5: Move Files to New Structure](5_move_files.md)

---

## ✅ Final Output Includes:

* `data/file_index.csv`: Raw file metadata and tags
* `output/final_structure.html`: Preview of organized structure
* All modular Python scripts in `scripts/`
* Ready-to-push structure for GitHub + docs

---

👉 Now continue to: [1\_setup\_llm.md](1_setup_llm.md)
