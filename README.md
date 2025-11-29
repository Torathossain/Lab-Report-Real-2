# ID-CSE412-223E2-LabReport02: Flower Classification using K-Nearest Neighbors (KNN)

## 🎯 Assignment Objective

This repository contains the code and supporting files for **Lab Report 02** in **CSE 412 (Machine Learning/Data Mining)**.

The primary objective was to implement the **K-Nearest Neighbors (KNN)** algorithm for a multi-class classification problem using the **Iris Flower dataset**. The goal included a systematic investigation into the impact of the **Train:Test split ratio** and the hyperparameter **$k$** on model performance, ultimately identifying the optimal configuration.

## 🗃️ Repository Contents

| File Name | Description |
| :--- | :--- |
| `knn_classifier.py` | The main Python script that loads the Iris dataset, performs preprocessing (scaling), iterates through all specified ratios and $k$ values, and reports the optimal parameters and final evaluation metrics. |
| `knn_optimal_metrics.csv` | Output file summarizing the optimal parameters found and the resulting evaluation metrics (Accuracy, Precision, Recall, F1-Score). |
| `README.md` | This file, providing an overview of the assignment and methodology. |

---

## 💻 Methodology

The implementation focused on robust preprocessing and exhaustive hyperparameter tuning.

### 1. Data and Preprocessing

* **Dataset:** Iris Flower Dataset (Built-in to `scikit-learn`).
* **Missing Values:** Checked for missing values and confirmed none were present.
* **Scaling:** **Min-Max Scaling** was applied to all four numeric features (`sepal length`, `sepal width`, `petal length`, `petal width`) to normalize the data between 0 and 1. This is crucial for distance-based algorithms like KNN.
    $$X_{\text{scaled}} = \frac{X - X_{\text{min}}}{X_{\text{max}} - X_{\text{min}}}$$

### 2. Model Tuning & Evaluation

The KNN model was systematically evaluated across two key factors:

| Parameter | Values Used | Description |
| :--- | :--- | :--- |
| **Split Ratios (Train:Test)** | $50:50, 60:40, 70:30, 80:20$ | Ratios used to split the dataset for training and testing the model. |
| **k (Number of Neighbors)** | $1, 3, 5, 7, 9, 11, 13, 15$ | Odd values of $k$ were tested to prevent ties in the majority vote. |

The best combination was determined by the highest overall **Accuracy**.

---

## 📈 Optimal Results

The exhaustive search identified the following configuration as optimal:

| Metric | Value |
| :--- | :--- |
| **Optimal $k$** | **7** |
| **Best Ratio (Train:Test)** | **80:20** |
| **Highest Accuracy** | **1.0000** |

### Final Evaluation Metrics

The final model ($k=7$ with 80:20 split) achieved perfect scores on the test set:

| Metric | Value |
| :--- | :--- |
| **Accuracy** | $1.0000$ |
| **Precision (Weighted)** | $1.0000$ |
| **Recall (Weighted)** | $1.0000$ |
| **F1-Score (Weighted)** | $1.0000$ |

### Confusion Matrix

The confusion matrix confirms zero misclassifications in the test set (Perfect classification):

$$\text{Confusion Matrix} = \begin{pmatrix}
10 & 0 & 0 \\
0 & 10 & 0 \\
0 & 0 & 10
\end{pmatrix}$$
*(Rows and columns correspond to the three Iris species.)*

---

## ⚙️ How to Run the Code

1.  **Prerequisites:** Ensure you have Python installed, along with the required libraries (`pandas`, `numpy`, `scikit-learn`).
    ```bash
    pip install pandas numpy scikit-learn
    ```
2.  **Setup:** Save the provided Python script as `knn_classifier.py`.
3.  **Execution:** Run the script from your terminal:
    ```bash
    python knn_classifier.py
    ```
4.  **Output:** The script will print the tuning results and final evaluation metrics to the console, and save the optimal results to `knn_optimal_metrics.csv`.

---

## 📝 Submission Requirement

The final submission is the PDF file named **`[YourID]-CSE412-223E2-LabReport02-knn.pdf`**, which includes a detailed report of this methodology, theoretical background (including equations), and analysis of these results.
