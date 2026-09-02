# DNA Sequence Classification Using VirusBERT and Transformer-CNN

## Overview

This project focuses on **viral DNA sequence classification using deep learning and Transformer-based architectures**. The system processes genomic sequences and classifies them into six different virus categories using **K-mer encoding, Transformer attention mechanisms, and CNN-based feature extraction**.

The project combines techniques from **bioinformatics, natural language processing (NLP), and deep learning** to learn meaningful patterns from viral genome sequences.

## Virus Classes

The model is designed to classify sequences into the following six classes:

* SARS-CoV-1
* SARS-CoV-2
* MERS
* Ebola
* Dengue
* Influenza

## Project Architecture

The overall pipeline follows:

```text
NCBI Viral Genome Data
        ↓
Sequence Preprocessing
        ↓
DNA Sequence Cleaning
        ↓
K-mer Encoding (K=3)
        ↓
Token & Position Embedding
        ↓
Transformer Block
        ↓
Conv1D Feature Extraction
        ↓
MaxPooling1D
        ↓
Global Average Pooling
        ↓
Dense Layer
        ↓
Softmax Classification
        ↓
Virus Class Prediction
```

## Dataset

Viral genome sequences were collected using the **NCBI Entrez API through BioPython**.

The dataset contains genomic sequences from six virus categories:

| Class | Virus      |
| ----- | ---------- |
| 0     | SARS-CoV-1 |
| 1     | SARS-CoV-2 |
| 2     | MERS       |
| 3     | Ebola      |
| 4     | Dengue     |
| 5     | Influenza  |

The data collection and preprocessing pipeline was designed to obtain multiple genome sequences for each virus category.

## Data Preprocessing

The following preprocessing techniques were implemented:

1. Retrieved viral genome sequences from NCBI.
2. Removed invalid or unwanted nucleotide characters.
3. Converted sequences into a standardized format.
4. Generated **3-mer sequences** from genomic DNA.
5. Converted K-mers into numerical representations.
6. Applied sequence padding/truncation to maintain consistent input dimensions.
7. Split the dataset into training and testing sets.

### K-mer Encoding

A K-mer represents a continuous sequence of `K` nucleotides.

For example, with `K=3`:

```text
DNA Sequence:
ATGCGAT

3-mers:
ATG
TGC
GCG
CGA
GAT
```

This representation allows the deep learning model to learn local patterns within genomic sequences.

## Model Architecture

The primary architecture combines **Transformer and CNN components**.

### Transformer Component

The Transformer block consists of:

* Token Embedding
* Positional Embedding
* Multi-Head Self-Attention
* Feed-Forward Neural Network
* Layer Normalization
* Residual Connections

The Transformer helps the model learn relationships between different regions of the DNA sequence.

### CNN Component

After Transformer feature extraction, convolutional layers are used to identify local sequence patterns.

```text
Transformer Output
       ↓
Conv1D
       ↓
MaxPooling1D
       ↓
GlobalAveragePooling1D
       ↓
Dense
       ↓
Softmax
```

## Model Configuration

Example configuration used during experimentation:

```text
Embedding Dimension : 50
Number of Heads     : 2
Feed Forward Dim    : 16
K-mer Size          : 3
CNN Filters         : 32 / 64 / 128
Pooling Window      : 4
Number of Classes   : 6
Optimizer           : Adam
Learning Rate       : 0.003
```

Multiple model configurations were experimented with to compare classification performance.

## Training

The models were trained using **TensorFlow/Keras**.

Training techniques included:

* Adam optimizer
* EarlyStopping
* ReduceLROnPlateau
* ModelCheckpoint
* Mini-batch training

Example configuration:

```text
Batch Size : 4
Epochs     : 20–30
Optimizer  : Adam
```

## Technologies Used

### Programming Language

* Python

### Deep Learning

* TensorFlow
* Keras
* Transformer Architecture
* Convolutional Neural Networks (CNN)

### Bioinformatics

* BioPython
* NCBI Entrez
* Viral genome sequence processing
* K-mer encoding

### Machine Learning

* Scikit-learn
* Random Forest
* Train/Test Splitting
* Model Evaluation

### Data Processing

* NumPy
* Pandas
* Pickle

## Project Structure

```text
DNA-Sequence-Classification/
│
├── data/
│   ├── X_train_k3.pkl
│   └── Y_train_k3.pkl
│
├── models/
│   ├── transformer_cnn_k3_32f_4pool
│   ├── transformer_cnn_k3_64f_4pool
│   ├── transformer_cnn_k3_128f_4pool
│   └── cnn_k3_2layers
│
├── notebooks/
│   └── DNA_Virus_Classification.ipynb
│
├── src/
│   ├── data_collection.py
│   ├── preprocessing.py
│   ├── kmer_encoding.py
│   ├── model.py
│   └── evaluation.py
│
├── requirements.txt
├── README.md
└── .gitignore
```

## Key Features

* Viral genome sequence classification
* NCBI genome data collection
* Automated DNA sequence preprocessing
* 3-mer sequence encoding
* Transformer-based sequence representation
* CNN-based feature extraction
* Multi-class virus classification
* Model checkpointing
* Learning-rate optimization
* Early stopping
* Experimental comparison of different architectures

## Results

The project evaluates multiple deep learning architectures by comparing their classification performance across the six virus categories.

The experimental models include:

* Transformer + CNN with 32 filters
* Transformer + CNN with 64 filters
* Transformer + CNN with 128 filters
* Two-layer CNN baseline

Performance can be evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

> **Note:** Add your final test accuracy, precision, recall, and F1-score here once the final model results are confirmed.

## Applications

This approach can be applied to:

* Viral genome classification
* Bioinformatics research
* Pathogen identification
* Genome sequence analysis
* Computational biology
* Automated viral sequence screening

## Future Improvements

Future development can include:

* Training on larger genomic datasets
* Using larger pretrained DNA language models such as **DNABERT**
* Hyperparameter optimization
* Transfer learning
* Attention visualization
* Explainable AI for genomic classification
* Deployment as a REST API
* Real-time sequence classification

## Installation

Clone the repository:

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd DNA-Sequence-Classification
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

## Usage

Run the preprocessing pipeline:

```bash
python src/preprocessing.py
```

Train the model:

```bash
python src/model.py
```

Evaluate the trained model:

```bash
python src/evaluation.py
```

## Example Prediction

```text
Input DNA Sequence:
ATGCGTACGATCGATCG...

Predicted Virus:
SARS-CoV-2

Confidence:
0.94
```

## Research Objective

The primary objective of this project is to investigate how **Transformer-based deep learning models combined with CNNs can learn discriminative patterns from viral genomic sequences** and improve automated multi-class virus classification.

## Author

**Vinay Kumar Lachannagari**

### Skills Demonstrated

`Python` · `TensorFlow` · `Keras` · `Transformers` · `CNN` · `BioPython` · `NCBI Entrez` · `Scikit-learn` · `NumPy` · `Pandas` · `Bioinformatics` · `Deep Learning` · `DNA Sequence Classification`

