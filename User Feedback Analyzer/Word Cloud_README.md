# 📊 EdTech Feedback Analyzer (English, Bangla & Banglish)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/YOUR_REPO_NAME/blob/main/WordCloud.ipynb)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Library](https://img.shields.io/badge/BNLP-Toolkit-green)

A specialized Natural Language Processing (NLP) tool designed to analyze customer feedback for EdTech platforms in Bangladesh. It processes mixed-language datasets (English, Bengali, and phonetic "Banglish") to generate high-resolution semantic Word Clouds, providing stakeholders with immediate visual insights into user sentiment.

---

## 🧐 The Challenge: Rendering Complex Bengali Script
One of the core engineering challenges in this project was handling **Complex Text Layout (CTL)** for the Bengali language.

### 🔴 The Problem
Standard Python libraries (`matplotlib`, `wordcloud`) often fail to render Bengali "Juktakkhor" (conjuncts) correctly on Windows environments.
* **Issue 1:** Letters appear broken or separated (e.g., `ক্ষ` rendering as `ক` + `ষ`).
* **Issue 2:** "Tofu" artifacts (square boxes `□□□`) appear due to missing font glyphs.
* **Root Cause:** The standard Windows Python environment lacks the `libraqm` library, which is essential for shaping complex scripts.

### 🟢 The Solution
To ensure production-grade visualizations, I engineered a Linux-based pipeline on **Google Colab**:
1.  **Environment:** Migrated to a Linux environment to leverage `libraqm`, `HarfBuzz`, and `FriBiDi` text shaping engines.
2.  **Tokenization:** Replaced standard whitespace splitting with **`bnlp_toolkit`**, a dedicated tokenizer for Bengali, ensuring grammatical accuracy.
3.  **Font Engineering:** Integrated the **Kalpurush** TrueType font to force correct Unicode rendering.

## 🧐 The Challenge: Rendering Complex Bengali Script
One of the core engineering challenges in this project was handling **Complex Text Layout (CTL)** for the Bengali language.

### 🔴 The Problem
Standard Python libraries (`matplotlib`, `wordcloud`) often fail to render Bengali "Juktakkhor" (conjuncts) correctly on Windows environments.
* **Issue 1:** Letters appear broken or separated (e.g., `ক্ষ` rendering as `ক` + `ষ`).
* **Issue 2:** "Tofu" artifacts (square boxes `□□□`) appear due to missing font glyphs.
* **Root Cause:** The default text engine on Windows does not support complex Bengali shaping out of the box.

### 🟢 The Solution
To ensure production-grade visualizations, I implemented a three-step fix:
1.  **Environment Strategy:** Migrated the rendering pipeline to **Google Colab (Linux)**. Unlike Windows, the Linux environment correctly handles complex character shaping for Bengali script without requiring manual system patches.
2.  **Advanced Tokenization:** Instead of simple whitespace splitting (which breaks Bengali grammar), I implemented **`bnlp_toolkit`**. This library accurately tokenizes Bengali text, ensuring words are separated logically before visualization.
3.  **Font Engineering:** Integrated the **Kalpurush** TrueType font to force correct Unicode rendering, replacing the incompatible default system fonts.

---

## 🚀 Key Features
* **Multi-Language Support:** Seamlessly handles English, native Bangla, and Banglish in the same dataset.
* **Smart Stopword Filtering:** Uses a hybrid filter removing common English (e.g., "the", "is") and Bangla (e.g., "এবং", "করা") noise words.
* **Production-Ready Output:** Exports images at **300 DPI** (Print Quality), suitable for professional business reports.
* **Automated Data Pipeline:** Auto-cleans `NaN` values and normalizes text types during ingestion.

---

## 🛠️ Tech Stack
* **Core:** Python 3.10+
* **Data Processing:** Pandas (ETL), NumPy
* **NLP:** BNLP Toolkit (Bengali Natural Language Processing)
* **Visualization:** WordCloud, Matplotlib (with Libraqm backend)

## 📊 Sample Output
![Sample Word Cloud](Cloud_Sample.png)

## 📂 Project Structure
```text
├── WordCloud.ipynb      # Core analysis script (Optimized for Colab)
├── reviews.xlsx         # Dataset (Requires 'Company' and 'Review' columns)
├── kalpurush.ttf        # Essential font for Bengali rendering
└── Cloud_Sample.png     # Sample output for documentation
