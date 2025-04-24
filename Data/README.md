# Datasets

This folder contains preprocessed and class-imbalanced versions of three text-classification datasets:

1. **ISOT Fake News Headlines (Fake News Detection)**
2. **Hate Speech Detection**
3. **Emotion Detection**

The following described preprocessing that was performed can be found in [`SyntheticDataGeneration-DatasetsPreprocessing.ipynb`](https://github.com/RohitP123/Synthetic-Data-Generation-Techniques-Analysis/blob/main/Data/SyntheticDataGeneration_DatasetsPreprocessing.ipynb)

Original Datasets can be found at:
1. [ISOT Fake News](https://www.kaggle.com/datasets/emineyetm/fake-news-detection-datasets)
2. [Hate Speech Detection](https://github.com/Vicomtech/hate-speech-dataset/tree/master)
3. [Emotion Detection](https://www.kaggle.com/datasets/praveengovi/emotions-dataset-for-nlp)

---

## 1. ISOT Fake News Headlines

- **Source files**: (in ISOT folder)  
  - `Fake.csv` (23481 fake news examples)  
  - `Real.csv` (21417 real news examples)  
  Each file has columns: `title`, `text`, `subject`, `date`.

- **Preprocessing**:
  1. Added a binary `label` column: `0` = fake, `1` = real.
  2. Combined both csv's into a single csv keeping only title and label.
  3. Downsampled to create two csv's:
     - **Fake-dominant** (`isot_fake_dominant_0_1.csv`): 1000 fake + 200 real.
     - **Real-dominant** (`isot_real_dominant_0_1.csv`): 200 fake + 1000 real.
  4. Also created another 2 csv that instead of having numeric labels, it has string labels of "Fake" and "Real"
     - Called `isot_real_dominant_real_fake.csv` and `isot_fake_dominant_real_fake.csv`

---

## 2. Hate Speech Detection

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
  3. Data was already imbalanced (9507 noHate and 1196 hate) so created `hate_speech_0_1.csv` from this.
      - Downsampled to contain 1000 noHate data points and 200 hate datapoints.
  5. Also created a csv that contained string labels of "no hate" and "Hate" called `hate_speech_hate_nohate.csv`
 
---

## 3. NLP Emotion Classification Dataset

- **Source file**: `train.txt`, `test.txt`, `val.txt` (after unzipping original dataset)
  Format: text; label

- **Preprocessing**:
  1. Loaded the txt files
  2. Combined them and extract text into a column and label into another column
  3. There are 6 labels for emotions in this dataset (joy, sadness, anger, fear, love, surprise)
  5. Created one artificially imbalanced datasets:
     - `emotion_multiclass_dataset.csv`
         - contains 100 surprise data points (minority) and 300 data points for each of the other categories. 

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



