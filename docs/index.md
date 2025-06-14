<!-- Link global solarized theme -->
<link rel="stylesheet" href="./assets/css/style.css">

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
├── documentation/
│   ├── index.md
│   ├── 1_setup_llm.md
│   ├── 2_scan_directory.md
│   ├── 3_tag_files.md
│   ├── 4_generate_html.md
│   └── 5_move_files.md
├── src/
│   ├── scripts/
│   │   ├── scan_directory.py
│   │   ├── tag_generator.py
│   │   ├── html_generator.py
│   │   ├── file_mover.py
│   │   └── utils.py
│   ├── data/
│   │   └── file_index.csv
│   ├── templates/
│   │   └── structure_template.html
│   └── output/
│       └── final_structure.html
```

---

## 🧭 TagPi Documentation Index

Welcome to the **TagPi** documentation! This index links to all major components of the project.

### 📚 Modules

- [📁 Overview and Architecture](./index.md)
- [🛠 Step 1: Setup Lightweight LLM](./1_setup_llm.md)
- [📂 Step 2: Scan Directory and Extract Metadata](./2_scan_directory.md)
- [🏷️ Step 3: Tag Files Based on Filename](./3_tag_files.md)
- [🌐 Step 4: Generate Static HTML View](./4_generate_html.md)
- [🚚 Step 5: Move Files to New Tagged Structure](./5_move_files.md)

### 🔗 Related Files

- [README.md](../README.md)
- [HTML Template Preview](../src/output/final_structure.html)
- [Raw File Index (CSV)](../src/data/file_index.csv)

---
