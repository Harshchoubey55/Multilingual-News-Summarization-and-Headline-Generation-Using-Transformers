# Multilingual News Summarization and Headline Generation Using Transformers

## Overview

This project implements an end-to-end Natural Language Processing (NLP) pipeline for **abstractive news summarization**, **headline (hook) generation**, and **multilingual translation** using modern Transformer-based models.

The system leverages **transfer learning** to efficiently generate high-quality summaries and engaging headlines from long-form news articles, and then translate them into multiple target languages. The pipeline is designed to be modular, lightweight, and extensible for research, learning, and real-world applications.

---

## Key Objectives

* Automatically summarize long news articles into concise, readable summaries
* Generate short, attention-grabbing headlines from summaries
* Translate summaries and headlines into multiple languages
* Demonstrate practical usage of pre-trained Transformer models without expensive training

---

## Core Features

### 1. Abstractive Text Summarization

The project uses a pre-trained **Text-to-Text Transformer (T5)** model to perform abstractive summarization. Unlike extractive methods, the model generates new sentences that capture the core meaning of the original article.

### 2. Headline / Hook Generation

From the generated summary, the system produces a short, catchy headline intended to encourage users to click and read the full article. This step uses prompt-based text generation with the same Transformer model.

### 3. Multilingual Translation

Both the summary and the generated headline can be translated into multiple languages using a pre-trained multilingual neural machine translation model.

### 4. Dataset-Based Demonstration

The pipeline is demonstrated using a subset of the **CNN/DailyMail** dataset, a standard benchmark for news summarization tasks.

---

## Models Used

### Summarization and Headline Generation

* **Model:** `t5-small`
* **Type:** Sequence-to-sequence Transformer
* **Purpose:**

  * Abstractive summarization
  * Prompt-based headline generation

### Translation

* **Model:** `Helsinki-NLP/opus-mt-en-mul`
* **Type:** Multilingual Neural Machine Translation
* **Purpose:** Translate English summaries and headlines into multiple languages

---

## Dataset

* **CNN/DailyMail Dataset**

  * Widely used benchmark dataset for news summarization
  * Contains news articles paired with human-written summaries
  * Only a small percentage of the dataset is loaded to reduce runtime and memory usage

---

## Installation

Install the required dependencies using:

```bash
pip install transformers datasets nltk
```

Download the necessary NLTK resources:

```python
import nltk
nltk.download("punkt")
```

---

## Pipeline Workflow

1. **Data Loading**
   News articles and reference summaries are loaded from the CNN/DailyMail dataset.

2. **Summarization**
   Each article is passed to the T5 model to generate a concise abstractive summary.

3. **Headline Generation**
   A short, engaging headline is generated using the summary as input.

4. **Translation**
   The generated summary and headline are translated into a selected target language.

5. **Output Display**
   For each article, the following are displayed:

   * Truncated original article
   * Generated summary
   * Generated headline
   * Translated summary
   * Translated headline
   * Reference (ground-truth) summary

---

## Supported Languages

The translation module supports multiple languages via standard language codes.

Examples include:

| Language  | Code |
| --------- | ---- |
| Hindi     | hi   |
| French    | fr   |
| Spanish   | es   |
| German    | de   |
| Bengali   | bn   |
| Malayalam | ml   |
| Tamil     | ta   |

The target language can be changed directly in the code:

```python
target_lang_code = "hi"
```

---

## Design Choices

* **Transfer Learning:**
  Avoids training from scratch, reducing compute requirements.

* **Single-Model Reuse:**
  The same Transformer model is used for both summarization and headline generation using task-specific prompts.

* **Modular Functions:**
  Each stage (summarization, headline generation, translation) is implemented as a separate function for clarity and extensibility.

---

## Potential Extensions

* Replace `t5-small` with larger models such as `facebook/bart-large-cnn` or `google/pegasus-xsum`
* Add evaluation metrics such as ROUGE or BLEU once environment issues are resolved
* Build a web interface using Streamlit or FastAPI
* Integrate real-time news sources via APIs
* Store outputs in CSV or JSON for analytics pipelines

---

## Use Cases

* News aggregation platforms
* Multilingual content publishing systems
* Media analytics and summarization tools
* NLP experimentation and academic projects
* Resume-ready applied NLP projects

---

## License

This project is intended for **educational and research purposes**.
You are free to modify, extend, and adapt it for non-commercial use.
