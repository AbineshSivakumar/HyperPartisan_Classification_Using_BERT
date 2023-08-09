# HyperPartisan Classification Using BERT-Based Methods and Longformers

This repository contains the code and resources for developing a hyperpartisan news article classification system leveraging state-of-the-art transformer models like BERT, ROBERTa, and Longformer.

## Objective

The primary goal of this project is to accurately classify news articles as hyperpartisan or non-hyperpartisan. The project explores and compares the performance of various transformer models and assesses the impact of incorporating Part-of-Speech (POS) tagging on classification accuracy.

## Tools and Models

The project was implemented using the following tools and models:

- **Programming Language:** Python
- **Library:** Huggingface datasets
- **Models:**
  - BERT (Bidirectional Encoder Representations from Transformers)
  - ROBERTa (A Robustly Optimized BERT Pretraining Approach)
  - Longformer (The Long-Document Transformer)

## Methods

### Method 1: Segment-Based Evaluation
We divide the text into 512-token segments and evaluate the performance of our models on these segments. This method helps us identify which parts of the document influence categorization accuracy.

### Method 2: Summarization-Based Approach
We condense the documents into summaries of 512 tokens each using the Hugging Face summarization pipeline. This summarized version is used for classification tasks.

### Method 3: Stride-Based Segmentation
We refer to each 512-token segment of a document and introduce a 'stride' that represents the shared tokens between consecutive segments. This method allows us to handle documents of varying lengths.

## Detailed Report
A comprehensive report detailing the methods, experiments, and results is available in this repository. Please refer to the [report](https://github.com/AbineshSivakumar/HyperPartisan_Classification_Using_BERT/tHyperpartisan-Classification-report.pdf) for a complete understanding of the project.



## Outcome

- **Hyperpartisan Classification System:** Developed a robust system capable of classifying news articles into hyperpartisan or non-hyperpartisan categories.
- **Comparative Analysis:** Conducted a detailed comparison between BERT and ROBERTa models to understand their strengths and weaknesses.
- **Longformer Exploration:** Investigated the effectiveness of Longformer in handling lengthy news articles, a common challenge in text classification tasks.

## Getting Started

### Prerequisites

- Python 3.x
- Huggingface datasets library
- PyTorch

### Installation

1. Clone the repository:
   ```bash
     git clone https://github.com/AbineshSivakumar/HyperPartisan_Classification_Using_BERT
   ```
2. Install all the necessary packages
   ```bash
     pip install -r requirements.txt
   ```

### Usage

Run into each method and execute the respective jupyter notebooks

