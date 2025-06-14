## 🛠 Step 1: Setup Lightweight LLM on Raspberry Pi 4

Install dependencies:

```bash
sudo apt update && sudo apt upgrade
sudo apt install python3 python3-pip git
pip3 install transformers torch pandas langdetect
```

Test BERT:

```python
from transformers import AutoTokenizer, AutoModel
model_name = "bert-base-multilingual-cased"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModel.from_pretrained(model_name)
text = "निवेदन_पत्र.pdf"
inputs = tokenizer(text, return_tensors="pt")
outputs = model(**inputs)
print(outputs.last_hidden_state.shape)
```

Optional (for sentence embeddings):

```bash
pip install sentence-transformers
```

```python
from sentence_transformers import SentenceTransformer
model = SentenceTransformer('sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2')
embedding = model.encode(["दस्तावेज़ नाम"])
```

---
