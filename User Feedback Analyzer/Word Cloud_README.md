# 📊 EdTech Feedback Analyzer (English, Bangla & Banglish)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/YOUR_REPO_NAME/blob/main/WordCloud.ipynb)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Library](https://img.shields.io/badge/BNLP--Toolkit-green)
![License](https://img.shields.io/badge/License-MIT-orange)

A specialized Natural Language Processing (NLP) tool designed to analyze customer feedback for EdTech platforms in Bangladesh. It processes mixed-language datasets (English, Bengali, and phonetic "Banglish") to generate high-resolution semantic Word Clouds, providing stakeholders with immediate visual insights into user sentiment.

---

## 🧐 The Engineering Challenge
One of the core challenges in this project was handling **Complex Text Layout (CTL)** for the Bengali language.

### 🔴 The Problem
Standard Python libraries (`matplotlib`, `wordcloud`) often fail to render Bengali "Juktakkhor" (conjuncts) correctly on Windows environments.
* **Issue 1:** Letters appear broken or separated (e.g., `ক্ষ` rendering as `ক` + `ষ`).
* **Issue 2:** "Tofu" artifacts (square boxes `□□□`) appear due to missing font glyphs.
* **Root Cause:** The default text engine on Windows does not support complex Bengali shaping out of the box.

### 🟢 The Solution
To ensure production-grade visualizations, I implemented a three-step fix:
1.  **Environment Strategy:** Migrated the rendering pipeline to **Google Colab (Linux)**. Unlike Windows, the Linux environment correctly handles complex character shaping for Bengali script without requiring manual system patches.
2.  **Advanced Tokenization:** Instead of simple whitespace splitting (which breaks Bengali grammar), I implemented **`bnlp_toolkit`**. This library accurately tokenizes Bengali text, ensuring words are separated logically before visualization.
3.  **Font Engineering:** Integrated the **Kalpurush** TrueType font to force correct Unicode rendering, replacing incompatible system fonts.

---

## 🚀 Key Features
* **Multi-Language Support:** Seamlessly handles English, native Bangla, and Banglish in the same dataset.
* **Smart Stopword Filtering:** Uses a hybrid filter removing common English (e.g., "the", "is") and Bangla (e.g., "এবং", "করা") noise words.
* **Production-Ready Output:** Exports images at **300 DPI** (Print Quality), suitable for professional business reports.
* **Automated Data Pipeline:** Auto-cleans `NaN` values, normalizes text types during ingestion, and handles missing file errors gracefully.

---

## ⚙️ Quick Start

### Option 1: Google Colab (Recommended)
This is the easiest way to run the project with perfect Bengali rendering.
1.  Click the **"Open in Colab"** badge at the top of this README.
2.  Upload your `reviews.xlsx` file to the file section.
3.  **Run All Cells**. The script will automatically download the required font and libraries.

### Option 2: Local Installation
If you prefer running it locally (Linux/Mac recommended):
```bash
# 1. Clone the repo
git clone [https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)

# 2. Install dependencies
pip install pandas matplotlib wordcloud bnlp_toolkit openpyxl

# 3. Add your data
# Place your 'reviews.xlsx' file in the folder

# 4. Run the script
python analyzer.py

## 🛠️ Tech Stack
* **Core:** Python 3.10+
* **Data Processing:** Pandas (ETL)
* **NLP:** BNLP Toolkit (Bengali Natural Language Processing)
* **Visualization:** WordCloud, Matplotlib

## 📊 Sample Output
![Sample Word Cloud](Cloud_Sample.png)

## 📂 Project Structure
```text
├── WordCloud.ipynb      # Core analysis script
├── reviews.xlsx         # Dataset (Requires 'Company' and 'Review' columns)
├── kalpurush.ttf        # Essential font for Bengali rendering
└── Cloud_Sample.png     # Sample output for documentation
