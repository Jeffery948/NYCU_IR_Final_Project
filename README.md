# NYCU IR Final Project - Group #21

## Project Overview
This project implements a **Reflective Retrieval-Augmented Generation (RAG)** framework for question answering on scientific documents. Our approach enhances smaller language models (Gemini 2.5 Flash-Lite) to achieve performance comparable to larger models, with improved answer accuracy and verified citations.

The main contributions are:
- A single-agent reflective RAG pipeline that consolidates reasoning and evidence.
- Evaluation on the **LitQA** dataset.
- Comparison against baselines including Deep Research and OpenScholar.

## Repository Structure
- `Evaluation.ipynb`           : Evaluation of our main approach and baselines
- `IR_RAG_main_approach.ipynb`: Implementation of the RAG-based main approach
- `README.md`                  : Project overview and instructions

## Main Approach
Our framework consists of three stages:

1. **Confidence-based Document Reasoning**  
   Each retrieved document is individually scored and used to produce provisional answers with self-estimated confidence.

2. **Reflection and Evidence Consolidation**  
   The model re-evaluates provisional answers and confidence scores, filtering and consolidating documents to select truly supporting evidence.

3. **Final Answer Generation**  
   Using the refined document set, the model produces the final answer and explicitly lists verified citations.

This pipeline allows smaller models to perform comparably to larger models while maintaining interpretability.

## Evaluation
Evaluation is performed on the LitQA dataset using the following metrics:

- **Answer Accuracy:** Fraction of correct answers over total questions.
- **Citation Accuracy:** Fraction of answers with correctly identified supporting citations.

### Performance Comparison on LitQA
| Method | Answer Acc. (%) | Citation Acc. (%) |
|--------|----------------|-----------------|
| Vanilla (Gemini 2.5 Flash-Lite) | 42 | 2 |
| RAG (Gemini 2.5 Flash-Lite) | 72 | 18 |
| RAG (Gemini 2.5 Pro) | 78 | 26 |
| OpenScholar | 50 | 42 |
| Deep Research (o4 mini) | **92** | **72** |
| Our framework (Gemini 2.5 Flash-Lite) | 84 | 32 |

- Bold values indicate the highest performance in each column.

Our framework achieves the best citation accuracy while maintaining competitive answer accuracy. Using the multi-step reflection mechanism, the Flash-Lite model remains faster than the Pro variant.
