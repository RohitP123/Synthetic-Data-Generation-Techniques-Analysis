# Datasets

This folder contains preprocessed and class-imbalanced versions of three text-classification datasets:

1. **Hate Speech Detection**
2. **Emotion Detection**
3. **Sarcasm Detection**

The following described preprocessing that was performed can be found in [`SyntheticDataGeneration-DatasetsPreprocessing.ipynb`](https://github.com/RohitP123/Synthetic-Data-Generation-Techniques-Analysis/blob/main/Data/SyntheticDataGeneration_DatasetsPreprocessing.ipynb)

Original Datasets can be found at:
1. [Hate Speech Detection](https://github.com/Vicomtech/hate-speech-dataset/tree/master)
2. [Emotion Detection](https://www.kaggle.com/datasets/praveengovi/emotions-dataset-for-nlp)
3. [Sarcasm Detection](https://www.kaggle.com/datasets/saurabhbagchi/sarcasm-detection-through-nlp?select=Sarcasm_Headlines_Dataset.json)

---

# Preprocessing

## 1. Hate Speech Detection

- **Within Hate Speech Dataset Folder** (after downloading from link above)
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
  3. Data was already imbalanced (9507 noHate and 1196 hate) so created `hate_speech_0_1-(minority_class_hate).csv` from this.
      - Downsampled to contain 1000 noHate data points and 200 hate datapoints.
  5. Also created a csv that contained string labels of "no hate" and "Hate" called `hate_speech_hate_nohate.csv`
 
---

## 2. NLP Emotion Classification Dataset

- **Source file**: `train.txt`, `test.txt`, `val.txt` (after unzipping original dataset)
  Format: text; label

- **Preprocessing**:
  1. Loaded the txt files
  2. Combined them and extract text into a column and label into another column
  3. There are 6 labels for emotions in this dataset (joy, sadness, anger, fear, love, surprise)
  5. Created one artificially imbalanced datasets:
     - `emotion_multiclass_imabalanced(minority_class_surprise).csv`
         - contains 100 surprise data points (minority) and 300 data points for each of the other categories. 

---


## 3. Sarcasm Detection

- **Source files**: (From download link  
  - `Sarcasm_Headlines_Dataset.json`  
  Each entry has: `article_link`, `headline`, `is_sarcastic`.

- **Preprocessing**:
  1. Extracted `headline` and `is_sarcastic` from JSON
  2. Chose sarcastic as minority class (0 - not sarcastic, 1 - sarcastic)
      - Downsampled to include 200 sarcastic and 1000 not sarcastic
  3. Made `sarcastic_numeric_labels(minority_class_sarcastic)` and `sarcastic_text_labels(minority_class_sarcastic)` for numeric and text labels respectively
 

Note, we also experimented with Sentiment using IMDB Movie Reviews and Fake News Detection using ISOT. However, we did not proceed with these due to movie reviews being long (taking time to process) and ISOT having issues with the dataset having semantic clues to classify which the model picks up on rather than understanding the text itself (leading to unreasonably high performance metrics). 


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



