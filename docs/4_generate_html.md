[← Home](./index.md) | [⬅ Previous](./3_tag_files.md) | [➡ Next](./5_move_files.md)
# 🌐 Step 4: Generate Static HTML View

`src/templates/structure_template.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Organized Files by Tag</title>
  <style>
    body { font-family: sans-serif; padding: 20px; }
    .tag-group { margin-bottom: 30px; }
    .tag { font-size: 1.5em; font-weight: bold; margin-bottom: 10px; }
    ul { list-style: none; padding-left: 20px; }
  </style>
</head>
<body>
  {% raw %}
  <h1>Organized Files by Tag</h1>
  {% for tag, files in tag_map.items() %}
    <div class="tag-group">
      <div class="tag">🗂 Tag {{ tag }}</div>
      <ul>
        {% for file in files %}
          <li>{{ file }}</li>
        {% endfor %}
      </ul>
    </div>
  {% endfor %}
{% endraw %}
</body>
</html>
```

`html_generator.py`

```python
import pandas as pd
from jinja2 import Environment, FileSystemLoader
import os

df = pd.read_csv('src/data/file_index.csv')
tag_map = {}
for _, row in df.iterrows():
    tag = row['tag']
    tag_map.setdefault(tag, []).append(row['filename'])

env = Environment(loader=FileSystemLoader('src/templates'))
template = env.get_template('structure_template.html')
output_html = template.render(tag_map=tag_map)

os.makedirs('src/output', exist_ok=True)
with open('src/output/final_structure.html', 'w', encoding='utf-8') as f:
    f.write(output_html)

print("✅ HTML visualization generated at src/output/final_structure.html")
```

---
[← Home](./index.md) | [⬅ Previous](./3_tag_files.md) | [➡ Next](./5_move_files.md)
