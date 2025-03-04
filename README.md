# 📚 RIIID Answer Correctness Prediction

This repository contains a **Knowledge Tracing** model that predicts whether students will answer questions correctly based on their **past performance** and **question metadata**. The project was developed using **machine learning techniques** on the **RIIID dataset**, which was part of the Kaggle competition: ["Riiid! Answer Correctness Prediction"](https://www.kaggle.com/c/riiid-test-answer-prediction).

## 🚀 Project Overview
- **Objective**: Model student knowledge over time and predict their future performance.
- **Dataset**: RIIID Education dataset, containing student interactions with an online education system.
- **Tech Stack**: Python, SQL, LightGBM, XGBoost, CatBoost, Data Preprocessing, Feature Engineering.
- **Performance Metric**: **AUC Score** (Area Under the Curve).

---

## 📌 **1. Introduction**
Traditional models of **knowledge estimation** assume that human learning is **static**, but **knowledge tracing** aims to dynamically model student learning. The challenge in this project is to use **data-driven approaches** to track student progress and **predict future correctness** in an **adaptive learning** environment.

The need for **personalized learning solutions** has grown significantly, especially after the **COVID-19 pandemic**, which disrupted education worldwide. **AI-powered tutoring systems** have the potential to bridge educational gaps by providing **personalized recommendations** and **adaptive learning paths**.

---

## 🎯 **2. Problem Statement**
Given:
- A student’s **historical performance**.
- The performance of **other students** on the same question.
- Metadata about each **question**.

**Goal**: Develop a model to predict whether a student will correctly answer their next question.

---

## 🔬 **3. Methodology**
The **Knowledge Discovery in Databases (KDD)** process was used iteratively to refine the model. This includes:
1. **Data Understanding**
2. **Data Preprocessing**
3. **Feature Engineering**
4. **Model Training & Evaluation**

---

## 🔍 **3.1 Data Preprocessing**
### **(a) Data Cleaning**
- Missing values in `prior_question_elapsed_time` were filled with a **global constant (-1)** for the first question per student.
- `prior_question_had_explanation` missing values were filled with **False**.
- Missing values in `tags` were filled using the **most frequent values** for that question part.

### **(b) Data Transformation**
- Boolean values in `prior_question_had_explanation` were converted to integers (`True → 1`, `False → 0`).
- `timestamp` and `prior_question_elapsed_time` were converted from **milliseconds to seconds**.

### **(c) Data Reduction**
- **Dropped unnecessary features** like `user_answer`, `row_id`, and `content_type_id` (low contribution to accuracy).
- Removed **redundant tags** (`Tag4`, `Tag5`, `Tag6`) that didn't improve model performance.

### **(d) Data Integration**
- Merged **train data** with **question metadata** to enrich features.

### **(e) Feature Extraction & Generation**
- **New features created**:
  - **User-based statistics**: `user_acc`, `user_correct_ratio`
  - **Question-based statistics**: `ques_acc`, `ques_correct_ratio`
  - **Time-based features**: `lagtime`, `attempt_no`
  - **Explanation impact**: `q_exp_correct`, `q_exp_acc`

---

## ⚙️ **3.2 Machine Learning Models**
Multiple models were tested in **two iterations (KDD1 & KDD2)**.

### **3.2.1 Models Tested in KDD1**
| Model         | AUC Score  |
|--------------|------------|
| **LightGBM** | **0.7700** |
| **CatBoost** | 0.7683     |
| **XGBoost**  | 0.7667     |
| AdaBoost     | 0.7650     |
| KNN          | 0.5940     |
| Naïve Bayes  | 0.5622     |
| Logistic Regression | 0.5543 |

👉 **Result**: LightGBM **performed best** in KDD1 with **AUC = 0.7700**.

---

### **3.2.2 Models Tested in KDD2 (After Feature Optimization)**
| Model         | AUC Score  |
|--------------|------------|
| **LightGBM** | **0.7900** |
| **CatBoost** | 0.7880     |
| **XGBoost**  | 0.7850     |

👉 **Result**: After additional feature engineering and fine-tuning, **LightGBM improved to AUC = 0.7900**, making it the **best-performing model**.

---

## 📊 **3.3 Performance Evaluation**
The final **LightGBM model** outperformed others in **both iterations**, proving its effectiveness in **student performance prediction**.

📈 **Key Insights**:
- **Feature Engineering** significantly improved model performance.
- **Time-based features** (lag time, attempt numbers) had a high impact on accuracy.
- **Student & question difficulty statistics** helped refine predictions.

---

## 🛠️ **4. Setup & Installation**
### **🔹 Step 1: Clone the Repository**
```bash
git clone https://github.com/Deepz12/RIIID-Answer-Correctness-Prediction.git
cd RIIID-Answer-Correctness-Prediction
