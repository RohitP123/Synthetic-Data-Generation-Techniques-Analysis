# Datasets

This folder contains preprocessed and class-imbalanced versions of three text-classification datasets:

1. **IMDB Movie Reviews (Sentiment Analysis)**
2. **ISOT Fake News Headlines (Fake News Detection)**
3. **Hate Speech Detection**

The following described preprocessing that was performed can be found in [`SyntheticDataGeneration-DatasetsPreprocessing.ipynb`](https://github.com/RohitP123/Synthetic-Data-Generation-Techniques-Analysis/blob/main/Data/SyntheticDataGeneration_DatasetsPreprocessing.ipynb)

---

## 1. IMDB Movie Reviews

- **Source file**: `IMDB-Dataset.csv`  
  Contains two columns:
  - `review`: movie review text  
  - `sentiment`: "positive" or "negative"

- **Preprocessing**:
  1. Loaded the CSV
  2. Split into positive and negative subsets (each contained 25000 data points).
  3. Created two artificially imbalanced datasets:
     - **Positive-dominant** (`imdb_unbalanced_positive_dominant.csv`): 20% of the original positive reviews + 100% of the negative reviews.
     - **Negative-dominant** (`imdb_unbalanced_negative_dominant.csv`): 100% of the original positive reviews + 20% of the negative reviews.

---

## 2. ISOT Fake News Headlines

- **Source files**: (in ISOT folder)  
  - `Fake.csv` (23481 fake news examples)  
  - `Real.csv` (21417 real news examples)  
  Each file has columns: `title`, `text`, `subject`, `date`.

- **Preprocessing**:
  1. Added a binary `label` column: `0` = fake, `1` = real.
  2. Combined both csv's into a single csv keeping only title and label.
  3. Created two imbalanced splits:
     - **Fake-dominant** (`isot_unbalanced_fake_dominant.csv`): 100% fake + 20% real.
     - **Real-dominant** (`isot_unbalanced_real_dominant.csv`): 20% fake + 100% real.

---

## 3. Hate Speech Detection

- **Within Hate Speech Dataset Folder**
  - **Source folder**: `all_files/`  
    Contains text files named `<file_id>.txt` with the speech.  
  - **Source CSV**: `annotations_metadata.csv`  
    Columns: `file_id`, `user_id`, `subforum_id`, `num_contexts`, `label`.
    Note these labels are manually labeled according to annotation guidelines.

- **Labels in original data**:
  - `noHate`  
  - `hate`  
  - `relation`  
  - `idk/skip`

- **Preprocessing**:
  1. Read each `<file_id>.txt` into a `text` column keeping only `noHate` or `hate` labels.
  2. Mapped `noHate → 0`, `hate → 1`.
  3. Data was already imbalanced (9507 noHate and 1196 hate) so created `hate_speech_unbalanced_noHate_dominant.csv` from this.


---
## Citations

```bibtex
@inproceedings{gibert2018hate,
    title = "{Hate Speech Dataset from a White Supremacy Forum}",
    author = "de Gibert, Ona  and
      Perez, Naiara  and
      Garc{\'\i}a-Pablos, Aitor  and
      Cuadros, Montse",
    booktitle = "Proceedings of the 2nd Workshop on Abusive Language Online ({ALW}2)",
    month = oct,
    year = "2018",
    address = "Brussels, Belgium",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/W18-5102",
    doi = "10.18653/v1/W18-5102",
    pages = "11--20",
}



