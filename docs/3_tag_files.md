# 🏷️ Step 3: Tag Files Based on Filename

```python
import pandas as pd
from sentence_transformers import SentenceTransformer
from sklearn.cluster import KMeans
import os

MODEL_NAME = 'sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2'
model = SentenceTransformer(MODEL_NAME)

df = pd.read_csv('src/data/file_index.csv')
filenames = df['filename'].tolist()
embeddings = model.encode(filenames)

def get_clusters(embeddings, n_clusters=10):
    kmeans = KMeans(n_clusters=n_clusters, random_state=0)
    labels = kmeans.fit_predict(embeddings)
    return labels

df['tag'] = get_clusters(embeddings)
df.to_csv('src/data/file_index.csv', index=False, encoding='utf-8-sig')
print("✅ Tags added to src/data/file_index.csv")
```

---
