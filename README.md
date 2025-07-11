# Coarse-Grained Word Sense Disambiguation

A transformer-based WSD system that clusters WordNet senses into coarse‐grained homonymy groups and augments BERT with part-of-speech embeddings to accurately resolve word meanings.

---

## Table of Contents

- [Project Overview](#project-overview)  
- [Objectives](#objectives)  
- [Dataset](#dataset)  
- [Methodology](#methodology)  
  - [Sense Clustering](#sense-clustering)  
  - [Model Architecture](#model-architecture)  
  - [POS-Tag Augmentation](#pos-tag-augmentation)  
---

## Project Overview

This repository implements a **coarse-grained Word Sense Disambiguation** system. By grouping fine-grained WordNet synsets into broader homonymy clusters, and by enriching a pre-trained BERT model with POS-tag embeddings, we achieve robust disambiguation performance on ambiguous English words.

## Objectives

1. **Sense Clustering**  
   - Aggregate WordNet synsets into coarse-grained homonymy groups to simplify the classification task and reduce label sparsity.  
2. **Transformer Fine-Tuning**  
   - Leverage a pre-trained BERT base model to encode sentence context and predict the correct coarse sense cluster.  
3. **POS-Tag Augmentation**  
   - Integrate part-of-speech information via dedicated embeddings to improve disambiguation of syntactically ambiguous tokens.  

## Dataset

- **WSD Task Dataset**  
  - English sentences annotated with WordNet sense keys.  
  - Train / Validation / Test splits provided by the shared task organizers.  
- **WordNet 3.0**  
  - Source of synset definitions and part-of-speech information.  

## Methodology

### Sense Clustering

1. **Extract** all synsets referenced in the training data.  
2. **Group** synsets sharing the same lemma and part-of-speech into a single coarse-grained class.  
3. **Assign** each annotated instance to its corresponding coarse-grained cluster.

### Model Architecture

- **Base Encoder**: `bert-base-uncased`, `RoBERTa-base` from Hugging Face Transformers.  
- **Classification Head**:  
  - Dropout layer
  - Dense layer mapping `[CLS]` token embedding + POS embedding to cluster logits  

### POS-Tag Augmentation

1. **POS Tagging**: Use spaCy to assign universal POS tags to each token.  
2. **Embedding Layer**: Learnable POS embedding (size 32) concatenated to BERT’s `[CLS]` representation before classification.
