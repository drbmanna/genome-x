# GENOME-X

Explainable machine learning for the effect of DNA mutations on CTCF binding.

## What this project does

We train a model to predict whether a short DNA sequence is bound by the transcription
factor CTCF, using public ENCODE data for K562 cells. We then change a single DNA letter
in a sequence, compare the model's prediction before and after, and explain which sequence
patterns drove the prediction.

The model learns patterns in data. A prediction does not prove that a mutation causes a
real biological effect. Results are reported with their limitations.

## Scope

In scope:

- One transcription factor (CTCF), one cell line (K562), one data source (ENCODE).
- Binary classification: bound vs not bound.
- A baseline model (Random Forest) before anything more complex.
- Per-prediction explanation of the single-letter comparison.

Out of scope (for now): lab validation, clinical diagnosis or treatment, causal claims,
other transcription factors, other cell lines.

## Pipeline

Public ENCODE data -> clean and prepare -> extract sequence features (k-mers, GC content)
-> train Random Forest -> evaluate (report the majority-class baseline first, then F1 and
ROC-AUC) -> compare an original sequence with a single-letter change -> explain the
prediction -> simple demonstration -> report.

## Repository layout

```
README.md          this file
data/README.md     how to obtain the data (the data itself is not committed)
notebooks/         exploration, one notebook per person
src/               reusable code, once it stabilizes
.gitignore
```

Data files are never committed. See `data/README.md`.

## Setup

1. Install Python 3 and the packages: pandas, numpy, scikit-learn, matplotlib.
2. Clone this repository to a local folder.
3. Follow `data/README.md` to download the dataset into `data/`.

## How we work

- `main` is protected. Nobody pushes to it directly.
- Each person works on their own branch, named `yourname/task`, for example
  `hazel/data-cleaning`.
- Open a pull request when a piece of work is ready. It gets reviewed, then merged.
- Record the exact command, the data source, the genome build, and the date whenever you
  download or process data. This is how the work stays reproducible.

## Team

- Shivangi Kala (CSE Data Science)
- Thameem Junaid (Information Technology)
- Madhu Yashni (Chemical Engineering)
- Kartik (Computer Science Engineering)
- Hazel (Biotechnology)

Guided by Bharat Manna, VIT Vellore.

## Learning resources

Biology:

- ENCODE Project portal (encodeproject.org): getting started, and what ChIP-seq measures.
- Rosalind (rosalind.info): learn FASTA parsing, k-mers, and GC content by coding.
- IUPAC nucleotide codes: A, C, G, T are bases; N means any base (unknown). N is not a
  mutation.

Machine learning:

- Fundamentals of ML, Google: https://developers.google.com/machine-learning
- scikit-learn user guide (scikit-learn.org): RandomForestClassifier, and model evaluation.
- SHAP documentation (shap.readthedocs.io): per-prediction explanation with TreeExplainer.
