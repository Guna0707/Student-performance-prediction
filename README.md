# Student Academic Performance Prediction using Machine Learning

## 📌 Project Overview

This project focuses on predicting student academic outcomes using **Machine Learning algorithms** and the **xAPI-Edu-Data dataset**.

The dataset contains information about **480 students**, including demographic details, academic information, classroom engagement, online learning activity, attendance, parent satisfaction, and overall performance.

The project compares seven machine learning algorithms across different prediction tasks:

* Linear Regression
* Logistic Regression
* Decision Tree
* Random Forest
* Support Vector Machine (SVM)
* K-Nearest Neighbors (KNN)
* Naive Bayes

---

## 🎯 Objectives

The main objectives of this project are:

1. Predict **Parent School Satisfaction** as Good or Bad.
2. Predict overall student **Performance Class** as Low, Middle, or High.
3. Analyze the relationship between student engagement activities.
4. Compare the performance of different machine learning algorithms.
5. Identify important factors affecting student academic outcomes.

---

## 📊 Dataset

### Dataset Name

**xAPI-Edu-Data.csv**

### Dataset Size

* **480 students**
* **17 columns**

The dataset includes information such as:

* Gender
* Nationality
* Place of Birth
* Stage
* Grade
* Section
* Topic
* Semester
* Raised Hands
* Visited Resources
* Announcements Viewed
* Discussion
* Parent Survey Response
* Parent School Satisfaction
* Student Absence Days
* Overall Performance Class

The main behavioural features used in the models include:

```text
raisedhands
Discussion
VisITedResources
AnnouncementsView
StudentAbsenceDays
Topic
```

These features were selected because they represent student engagement, online activity, attendance, and academic context.

---

## 🧠 Machine Learning Algorithms

### 1. Linear Regression

Linear Regression was used to predict the continuous **Discussion score** from:

* Raised Hands
* Visited Resources
* Announcements Viewed

It achieved:

```text
R² Score: 0.206
RMSE: 21.04
```

The model demonstrates a moderate positive relationship between student participation and discussion activity.

---

### 2. Logistic Regression

Logistic Regression was used to predict:

```text
Parent School Satisfaction
Good / Bad
```

Features:

```text
raisedhands
Discussion
VisITedResources
AnnouncementsView
Absence_enc
Topic_enc
```

Accuracy:

```text
80.2%
```

Logistic Regression was selected as an interpretable baseline classification model.

---

### 3. Decision Tree

Decision Tree was used to predict overall student performance:

```text
Low / Middle / High
```

Features:

```text
raisedhands
VisITedResources
AnnouncementsView
Discussion
Absence_enc
```

Accuracy:

```text
77.1%
```

The model also provides feature importance, helping identify which behavioural factors contribute most to performance prediction.

---

### 4. Random Forest

Random Forest was used for the same three-class performance prediction task:

```text
Low / Middle / High
```

Configuration:

```text
n_estimators = 200
max_depth = 7
```

Accuracy:

```text
75.0%
```

The same features as the Decision Tree were used so that both algorithms could be compared fairly.

---

### 5. Support Vector Machine (SVM)

SVM was used to predict:

```text
Parent School Satisfaction
Good / Bad
```

Configuration:

```text
Kernel = RBF
C = 1.0
Gamma = scale
```

Accuracy:

```text
77.1%
```

The features were standardized using `StandardScaler` before training.

---

### 6. K-Nearest Neighbors (KNN)

KNN was used to predict:

```text
Parent School Satisfaction
Good / Bad
```

Configuration:

```text
n_neighbors = 7
```

Accuracy:

```text
80.2%
```

Feature scaling was applied because KNN is a distance-based algorithm.

---

### 7. Naive Bayes

Gaussian Naive Bayes was used to predict:

```text
Parent School Satisfaction
Good / Bad
```

Accuracy:

```text
79.2%
```

Naive Bayes provides a probabilistic approach and was included to compare a different classifier family with Logistic Regression, SVM, and KNN.

---

## 📈 Model Performance

| Algorithm           | Target                     | Metric    |         Score |
| ------------------- | -------------------------- | --------- | ------------: |
| Linear Regression   | Discussion                 | R² / RMSE | 0.206 / 21.04 |
| Logistic Regression | Parent School Satisfaction | Accuracy  |         80.2% |
| Decision Tree       | Class (L/M/H)              | Accuracy  |         77.1% |
| Random Forest       | Class (L/M/H)              | Accuracy  |         75.0% |
| SVM                 | Parent School Satisfaction | Accuracy  |         77.1% |
| KNN                 | Parent School Satisfaction | Accuracy  |         80.2% |
| Naive Bayes         | Parent School Satisfaction | Accuracy  |         79.2% |

According to the project results, **Logistic Regression and KNN achieved the highest classification accuracy of 80.2%** for Parent School Satisfaction.

---

## 🔄 Project Workflow

```text
              ┌──────────────────────┐
              │   Load Dataset       │
              │  xAPI-Edu-Data.csv   │
              └──────────┬───────────┘
                         │
                         ▼
              ┌──────────────────────┐
              │   Data Exploration   │
              │ Shape / Data Types   │
              │ Class Distribution   │
              └──────────┬───────────┘
                         │
                         ▼
              ┌──────────────────────┐
              │ Data Preprocessing   │
              │ Label Encoding       │
              │ Feature Selection    │
              └──────────┬───────────┘
                         │
                         ▼
              ┌──────────────────────┐
              │ Train/Test Split     │
              │ 80% Training         │
              │ 20% Testing          │
              └──────────┬───────────┘
                         │
                         ▼
              ┌──────────────────────┐
              │ Feature Scaling      │
              │ StandardScaler       │
              └──────────┬───────────┘
                         │
                         ▼
        ┌────────────────┴────────────────┐
        │                                 │
        ▼                                 ▼
┌─────────────────┐              ┌────────────────────┐
│   Regression    │              │  Classification    │
│ Linear          │              │ Logistic Regression│
│ Regression      │              │ Decision Tree      │
└─────────────────┘              │ Random Forest      │
                                 │ SVM                │
                                 │ KNN                │
                                 │ Naive Bayes        │
                                 └─────────┬──────────┘
                                           │
                                           ▼
                                ┌────────────────────┐
                                │ Model Evaluation   │
                                │ Accuracy / R²      │
                                │ RMSE / Confusion   │
                                │ Matrix             │
                                └────────────────────┘
```

The common workflow includes loading the dataset, exploring the data, encoding categorical variables, selecting features, splitting the data into 80% training and 20% testing sets, scaling where required, training models, and evaluating their results.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Matplotlib**
* **Jupyter Notebook / Google Colab**
* **Git & GitHub**

---

## 📁 Project Structure

```text
Student-Academic-Performance-Prediction/
│
├── data/
│   └── xAPI-Edu-Data.csv
│
├── notebooks/
│   └── Student_Performance_ML.ipynb
│
├── src/
│   └── student_performance.py
│
├── results/
│   ├── linear_regression.png
│   ├── logistic_regression.png
│   ├── decision_tree.png
│   ├── random_forest.png
│   ├── svm.png
│   ├── knn.png
│   └── naive_bayes.png
│
├── Student_Performance_ML_Report.docx
├── requirements.txt
└── README.md
```

---

## 🚀 How to Run the Project

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/Student-Academic-Performance-Prediction.git
```

### Step 2: Open the Project

```bash
cd Student-Academic-Performance-Prediction
```

### Step 3: Install Required Libraries

```bash
pip install pandas numpy scikit-learn matplotlib
```

Or use:

```bash
pip install -r requirements.txt
```

### Step 4: Add the Dataset

Place the dataset inside the `data` folder:

```text
data/xAPI-Edu-Data.csv
```

### Step 5: Run the Python Program

```bash
python src/student_performance.py
```

You can also run the project using **Jupyter Notebook** or **Google Colab**.

---

## 📊 Key Findings

* Logistic Regression achieved **80.2% accuracy**.
* KNN also achieved **80.2% accuracy**.
* Naive Bayes achieved **79.2% accuracy**.
* Decision Tree achieved **77.1% accuracy**.
* SVM achieved **77.1% accuracy**.
* Random Forest achieved **75.0% accuracy**.
* Linear Regression achieved an **R² score of 0.206** for predicting Discussion.
* Student engagement and attendance features were consistently important across the models.

---

## 📌 Conclusion

This project demonstrates how different Machine Learning algorithms can be applied to student academic and behavioural data.

The results show that **Logistic Regression and KNN performed best for Parent School Satisfaction prediction**, while the **Decision Tree slightly outperformed Random Forest** for the three-class overall performance prediction on this particular test split.

The project also indicates that behavioural engagement features such as **raised hands, discussion participation, visited resources, announcements viewed, and attendance** are important factors for predicting student-related outcomes.

---

## 👨‍💻 Author

**GUNA T**

B.E. Computer Science and Engineering
**Cyber Security**

### Areas of Interest

* Cybersecurity
* Ethical Hacking
* Machine Learning
* Python
* Networking
* Web Security

---

## ⭐ Acknowledgement

This project was developed as an academic Machine Learning project using the **xAPI-Edu-Data student academic performance dataset**.

If you find this project useful, consider giving the repository a ⭐ on GitHub.
