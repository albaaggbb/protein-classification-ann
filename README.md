# Protein Expression Classification in Mice using Deep Learning

## 📌 Introduction  
This project implements and evaluates **artificial neural networks (ANNs)** to classify mice into **eight experimental groups** based on **protein expression and modifications** detected in the **nuclear fraction of the cortex**.  

The classification task involves 8 classes determined by three factors:  
- **Genotype**: control (c) or trisomic (t).  
- **Behavioral condition**: context-shock (CS) or shock-context (SC).  
- **Treatment**: memantine (m) or saline (s).  

The 8 classes are:  
1. **c-CS-s**: control – context-shock – saline  
2. **c-CS-m**: control – context-shock – memantine  
3. **c-SC-s**: control – shock-context – saline  
4. **c-SC-m**: control – shock-context – memantine  
5. **t-CS-s**: trisomic – context-shock – saline  
6. **t-CS-m**: trisomic – context-shock – memantine  
7. **t-SC-s**: trisomic – shock-context – saline  
8. **t-SC-m**: trisomic – shock-context – memantine  

The objective is the implementation and evaluation of **fully connected neural networks (dense layers)** for multiclass classification.  

## 📂 Dataset  
- `data3.csv`: Protein expression levels (1080 samples × 73 columns).  
  - Column 1: sample identifier.  
  - Columns 2–73: protein expression values.  
- `class3.csv`: Class labels (1080 samples × 1 column, values 1–8).  

No missing values are present in the dataset.  

## 🔍 Exploratory Data Analysis (EDA)  
- Summary statistics were computed for all protein features.  
- Class distribution was visualized (`class_distribution.png`).  
- Protein correlation analysis was performed (`correlation_matrix.png`).  

Outputs:  
- `summary_statistics.csv`  
- `class_distribution.png`  
- `correlation_matrix.png`  

## ⚙️ Data Preprocessing  
- Removal of sample ID column.  
- Normalization of protein features using **Min-Max scaling** to [0, 1].  
- Train-test split: 67% training (723 samples), 33% test (357 samples).  
- Encoding of class labels from 1–8 to integers 0–7.  

Normalized data is saved in `data_normalized.csv`.  

## 🧠 Models  

### Model 1 – Baseline Neural Network  
- **Input layer**: 72 protein features.  
- **Hidden layer**: Dense(35) with ReLU activation.  
- **Dropout layer**: Dropout(0.2).  
- **Output layer**: Dense(8) with softmax activation.  

**Parameters**:  
- Trainable parameters: 2,843  
- Optimizer: Adam  
- Loss function: Sparse categorical crossentropy  
- Epochs: 50  
- Validation split: 20%  

Outputs:  
- `learning_curve_model_1.png`  
- `confusion_matrix_model_1.png`  

### Model 2 – Extended Architecture  
- Deeper fully connected neural network with additional dense layers.  
- Same optimizer, loss function, and training procedure as Model 1.  

Outputs:  
- `learning_curve_model_2.png`  
- `confusion_matrix_model_2.png`  

## 📊 Evaluation  
Models were evaluated using:  
- Accuracy on test set  
- Confusion matrix  
- Precision, recall, and F1-score  

Visual outputs:  
- Training vs validation learning curves  
- Confusion matrices  

## 🛠️ Requirements  
- Python 3.9+  
- pandas  
- numpy  
- matplotlib  
- seaborn  
- scikit-learn  
- tensorflow  

Install dependencies:  
```bash
pip install -r requirements.txt
```

## 🚀 How to Run

1. Clone the repository:

```bash
git clone https://github.com/albaaggbb/protein-expression-classification.git
cd protein-expression-classification
```
2. Place `data3.csv` and `class3.csv` in the `data/` folder.

3. Run the notebook:

```bash
jupyter notebook notebooks/protein_expression_classification.ipynb
```

Results will be saved in the `results/` folder.

## 📌 Project Structure

├── data/
│   ├── data3.csv
│   └── class3.csv
├── notebooks/
│   └── protein_expression_classification.ipynb
├── results/
│   ├── class_distribution.png
│   ├── confusion_matrix_model_1.png
│   ├── confusion_matrix_model_2.png
│   ├── correlation_matrix.png
│   ├── data_normalized.csv
│   ├── learning_curve_model_1.png
│   ├── learning_curve_model_2.png
│   ├── summary_statistics.csv
│   └── protein_expression_classification.html
├── requirements.txt
└── README.md

## 👤 Author
Project developed by Alba Górriz. 