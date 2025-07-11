# Coarse-Grained-WSD 
*Transformer & POS-Augmented Word Sense Disambiguation*

---

## 🔍 Overview  
This project implements a **coarse-grained Word Sense Disambiguation** system on the NLP2023 dataset. We cluster WordNet senses into homonymy groups and fine-tune a BERT model augmented with POS-tag embeddings to predict the correct sense group for each target word.

---

## 📦 Features  
- **Homonymy Clustering**: Groups WordNet synsets into coarse-grained sense clusters.  
- **Transformer Backbone**: Fine-tunes a pre-trained BERT base model.  
- **POS Augmentation**: Concatenates POS-tag embeddings to the token embeddings before the classification head.  
- **End-to-End Pipeline**: From data preprocessing through model training to evaluation and inference.

---

## 🗄️ Dataset  
- **Format**: JSONL files with one example per line:  
  ```json
  {
    "sentence": "The bank raised interest rates.",
    "target_word": "bank",
    "pos": "NOUN",
    "gold_cluster": 3
  }
