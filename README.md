# Old vs New: Synthetic Data Augmentation for Class Balancing in Text Classification

This repository contains code and data for the analyzing traditional and LLM-based data augmentation techniques for mitigating class imbalance in text classification tasks.

## Project Overview
Class imbalance in text classification tasks (e.g., hate speech detection, sarcasm detection, emotion classification) often leads to poor performance on minority classes. This project systematically compares:
- **Traditional augmentation methods**: Back-translation, synonym replacement, word deletion, and combinations.
- **LLM-based techniques**: GPT-3.5 prompting strategies (class-driven, order-aware, and instruction-driven approaches).

Experiments are conducted on three imbalanced datasets, with evaluations focusing on minority-class F1 scores. For further details on datasets used, refer to the [README.md](https://github.com/RohitP123/Synthetic-Data-Generation-Techniques-Analysis/blob/main/Data/README.md) in the data folder.

## Repository Structure
```
├── data/ # Downsampled datasets and preprocessing scripts
│ ├── Augmented_Data # Contains the augmented data results for each traditional technique for each dataset
│ ├── Full_Data_with_Augments # Contains the original data and augmented data together as one csv.
| ├── SyntheticDataGeneration_DatasetsPreprocessing.ipynb # Preprocessing notebook for all datasets
│ └── README.md # Dataset details and preprocessing steps
│
├── Experiments/ # Google Colab notebooks for reproduction
│ ├── Traditional_Techniques_Data_Generation.ipynb # Back-translation, synonym replacement, etc.
│ └── LLM_Prompting_Experiments.ipynb # GPT-3.5 prompting strategies
│
├── README.md
```
