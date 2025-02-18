# A Comparative Study Between Multi-Agent and Single-Agent LLMs for ESG Report Analysis

## Overview
This project investigates the application of **Large Language Models (LLMs)** in automating **Environmental, Social, and Governance (ESG) report analysis**. We compare **Multi-Agent** and **Single-Agent** architectures to assess their effectiveness in extracting ESG insights. Our goal is to understand how each architecture processes ESG data rather than determining superiority.

## Abstract
This project explores ESG report analysis by deploying **Multi-Agent** and **Single-Agent** LLM architectures. The Multi-Agent system assigns specialized agents to each ESG category, whereas the Single-Agent model provides a holistic analysis. The evaluation compares their output to determine the impact on accuracy, interpretability, and efficiency.

## Dataset
- **Source**: ESG and sustainability reports from **50 NYSE-listed companies**.
- **Size**: ~75 pages per report.
- **Format**: Scraped from official websites and structured into ESG categories.
- **Gold Standard Data**: Human evaluations for **20 reports** were used for benchmarking.

## Methodology
### 1. Data Extraction and Preprocessing
- **Text Extraction**: PyMuPDF, SpaCy, NLTK
- **Categorization**: ESG-BERT Model, cosine similarity-based classification
- **Image Processing**: Tesseract OCR, CLIP (for visual ESG data)

### 2. ESG Classification
- **ESG-BERT**: Fine-tuned transformer model for ESG categorization.
- **all-MiniLM-L6-v2**: Efficient sentence embeddings.
- **CLIP Model**: Aligns visual and textual representations.

### 3. Agent Architecture
#### **Single-Agent Model**
- ESG data is directly processed by a single LLM for a **unified summary**.
#### **Multi-Agent Model**
- ESG data is divided among **three specialized agents** (E, S, G) for in-depth analysis.
- A final **Summary Agent** integrates individual agent insights into a complete ESG report.

## Evaluation Metrics
- **Summary Length**: Word count comparison.
- **Time Efficiency**: Processing time comparison.
- **Semantic Similarity**:
  - **BERTScore**: Measures content similarity.
  - **ROUGE-L**: Measures structural similarity.
- **Human Evaluation**:
  - **Summary Quality Score (1-5)**
  - **ESG Score Comparison**: LLM vs human ratings

## Results
| Metric | Multi-Agent | Single-Agent |
|--------|-------------|--------------|
| Time Taken | 35s (Gemma2:27B) / 27s (Llama3.2:3B) | 12s (Gemma2:27B) / 9s (Llama3.2:3B) |
| Length | 204 words | 211 words |
| Human Score | **4.25/5** | 4.00/5 |
| Score Difference | **0.25** | 0.40 |
| BERTScore | 0.87 | 0.87 |
| ROUGE Score | 0.31 | 0.31 |

## Conclusion
- **Multi-Agent models perform better for detailed ESG reports** but require **3x more processing time**.
- **Single-Agent models are more efficient** and provide comparable quality for standard reports.
- **Larger models (e.g., Gemma2:27B) outperform smaller ones (e.g., Llama3.2:3B)** in generating high-quality summaries.

## Future Work
- **Enhancing prompt engineering** with industry expert feedback.
- **Improving text extraction methodologies** to handle complex ESG reports.
- **Testing with higher-parameter models** such as Llama:70B and OpenAI/Gemini APIs.

## References
- **Fischbach et al.** - ESG-BERT: Transformer-based ESG report analysis.
- **OpenAI CLIP** - Vision-language alignment for image-text classification.
- **Hugging Face** - MiniLM and ESG-BERT model repositories.
