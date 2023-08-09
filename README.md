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

In the Hyperpartisan dataset, we refer to each 512-token segment of a given text as \( c_i \), where '\( i \)' denotes the segment's position in the sequence. We adhere to the maximum sequence length that BERT-based models can manage by setting the segment length to 512 tokens. We evaluate the performance of our models on these segments, allowing us to determine which portions of the document have the most influence on categorization accuracy. We assess the effectiveness of this BERT-based model on the first six segments (\( c_1 \) through \( c_6 \)), where \( c_1 \), \( c_2 \), etc., represent the first, second, and so on, 512-token segments of the documents. The median document length in the Hyperpartisan dataset is roughly 3000 tokens. For documents with a length less than \( i \times 512 \) tokens, we choose the final 512 tokens or fewer (in the case where \( i \) equals 1) for evaluation.

### Method 2: Summarization-Based Approach

In this approach, we condense the documents from the Hyperpartisan dataset into summaries of 512 tokens each. We employ the summarization pipeline from Hugging Face with its default parameters. The maximum sequence length this summarization model can accommodate is 1024 tokens. Therefore, we initially divide a document into several splits based on its length. We determine the number of splits \( n_i \) for a given document \( d_i \) as \( l_i / 1024 \), where \( l_i \) is the document's length. As the total length of a document's summarized version cannot exceed 512 tokens, we additionally compute the number of tokens per split \( nw_i \) for all splits of a specific document \( d_i \). We then concatenate all \( nw_i \)'s from a given document \( d_i \) to form the final summarized version. We use these summarized versions for both classification tasks.

### Method 3: Stride-Based Segmentation

In our approach, we refer to each 512-token segment of a given document from the Hyperpartisan dataset as \( c_i \), where 'i' indicates the position of the segment in the sequence. The 'stride' in this context refers to the block of tokens that are shared between any two segments, \( c_i \) and \( c_{i+1} \). As an example, let's take a stride value of 64. The tokens in \( c_1 \) and \( c_2 \), specifically \( c_1[448:512] \) and \( c_2[0:64] \), are identical if \( c_i[0:512] \) signifies the 512 tokens present in \( c_i \). In the case of a document \( d_i \) that is 1024 tokens in length, we would have three \( c_i' \)'s, as \( c_1[448:512] \) equals \( c_2[0:64] \) and \( c_2[448:512] \) equals \( c_3[0:64] \). For instance, \( d_i[0:512] \) is equivalent to \( c_1[0:512] \), \( d_i[448:512] \) is equivalent to \( c_2[0:64] \), \( d_i[512:960] \) is equivalent to \( c_2[64:512] \), \( d_i[896:960] \) is equivalent to \( c_3[0:64] \), and \( d_i[960:1024] \) equals \( c_3[64:128] \). Pad tokens are found in \( c_3[128:512] \). We execute our experiment up to about 3000 tokens, which mirrors the median length of documents in the Hyperpartisan dataset.


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

