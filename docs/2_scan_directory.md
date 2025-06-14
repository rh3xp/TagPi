<!-- Link global solarized theme -->
<link rel="stylesheet" href="./assets/css/style.css">

[← Home](./index.md) | [⬅ Previous](./1_setup_llm.md) | [➡ Next](./3_tag_files.md)
# 📂 Step 2: Scan Directory and Extract Metadata

```python
import os
import pandas as pd
from pathlib import Path

SUPPORTED_TYPES = ['.pdf', '.docx', '.jpg', '.png', '.txt', '.xlsx']

def scan_directory(base_path):
    records = []
    for root, _, files in os.walk(base_path):
        for file in files:
            ext = Path(file).suffix.lower()
            if ext in SUPPORTED_TYPES:
                full_path = os.path.join(root, file)
                records.append({
                    "filename": file,
                    "extension": ext,
                    "path": full_path,
                    "parent_folder": os.path.basename(root),
                    "size_kb": round(os.path.getsize(full_path) / 1024, 2)
                })
    return pd.DataFrame(records)

def save_to_csv(df, output_path='src/data/file_index.csv'):
    os.makedirs('src/data', exist_ok=True)
    df.to_csv(output_path, index=False, encoding='utf-8-sig')

if __name__ == "__main__":
    base_path = input("Enter the path to scan: ")
    df = scan_directory(base_path)
    save_to_csv(df)
    print(f"✅ {len(df)} files indexed and saved to src/data/file_index.csv")
```

---
[← Home](./index.md) | [⬅ Previous](./1_setup_llm.md) | [➡ Next](./3_tag_files.md)
