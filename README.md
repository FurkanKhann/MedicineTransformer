# 🧠 T5-Based Medicine Information Extractor

This project fine-tunes a **T5 Transformer model** to predict the **Uses** and **Side Effects** of medicines based on their **name** or **salt composition**.

---

## 📊 Task Description

- **Input**: Medicine name or salt composition  
  _(e.g., "Azithromycin (500mg)")_

- **Output**:
  _(Uses: Treatment of Bacterial infections; Side effects: Nausea Abdominal pain Diarrhea)_


---

## 🏗️ Model Architecture

- Model: `t5-small`  
- Library: 🤗 HuggingFace Transformers  
- Training Framework: PyTorch  
- Data Size: ~11,000 medicine records  
- Format: Custom dataset with fields:  
- Composition (input)  
- Uses (output)  
- Side effects (output)

---

## 📁 Model Files
```
t5_medicine_model/
├── config.json
├── pytorch_model.bin
├── tokenizer_config.json
├── special_tokens_map.json
├── spiece.model
├── generation_config.json
```


🔗 **[Download from Google Drive](https://drive.google.com/drive/folders/1MWHFk17R4QmovLXuOKrQx_JJOjC-YPdL?usp=sharing)**

## 📦 How to Use the Model

```python
from transformers import T5Tokenizer, T5ForConditionalGeneration

# Load from local path (after downloading from Google Drive)
model_path = "./t5_medicine_model"

tokenizer = T5Tokenizer.from_pretrained(model_path)
model = T5ForConditionalGeneration.from_pretrained(model_path)
model.eval()

# Inference
input_text = "Azithromycin (500mg)"
inputs = tokenizer(input_text, return_tensors="pt")

output_ids = model.generate(
    **inputs,
    max_length=128,
    decoder_start_token_id=model.config.decoder_start_token_id
)

result = tokenizer.decode(output_ids[0], skip_special_tokens=True)
print("Prediction:", result)
```
## 🧠 Future Work

- [ ] Deploy as an API using **FastAPI** or **Flask**
- [ ] Add a web UI using **Gradio** or **Streamlit**
- [ ] Improve accuracy using larger **Transformer models**
- [ ] Add **confidence scores** or implement **partial matching**

## 🧑‍💻 Author

**Furkan Khan**  
Model trained locally using **Python**, **HuggingFace Transformers**, and **PyTorch**

## 📜 Certification

This project was built and trained by **Khan F** as part of a personal initiative to explore Natural Language Processing using:

- ✅ Python  
- ✅ HuggingFace Transformers  
- ✅ PyTorch  

All training and testing were performed locally.  
This repository serves as a showcase of model development, deployment planning, and ongoing improvements in NLP.

> 📌 *This project is not officially certified by any institution and is intended for educational and demonstrative purposes.*

 

