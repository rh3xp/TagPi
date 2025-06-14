<!-- Link global solarized theme -->
<link rel="stylesheet" href="./assets/css/style.css">

[← Home](./index.md) | [⬅ Previous](./4_generate_html.md)
# 🚚 Step 5: Move Files to New Tagged Structure

```python
import os
import shutil
import pandas as pd

SRC_ROOT = "<your source path>"
DEST_ROOT = "organized_files"

os.makedirs(DEST_ROOT, exist_ok=True)

def safe_move(src, dest_dir, filename):
    os.makedirs(dest_dir, exist_ok=True)
    dest_path = os.path.join(dest_dir, filename)
    base, ext = os.path.splitext(filename)
    count = 1
    while os.path.exists(dest_path):
        dest_path = os.path.join(dest_dir, f"{base}_{count}{ext}")
        count += 1
    shutil.copy2(src, dest_path)

df = pd.read_csv('src/data/file_index.csv')
for _, row in df.iterrows():
    tag = row['tag']
    src_path = row['path']
    filename = row['filename']
    dest_dir = os.path.join(DEST_ROOT, f"tag_{tag}")
    safe_move(src_path, dest_dir, filename)

print(f"✅ Files moved to '{DEST_ROOT}' directory")
```

✅ You now have a complete open-source LLM-assisted file organizer ready to deploy on Raspberry Pi.

---
[← Home](./index.md) | [⬅ Previous](./4_generate_html.md)
