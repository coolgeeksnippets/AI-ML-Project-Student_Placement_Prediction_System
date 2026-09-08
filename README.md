# 🎓 Student Placement Prediction System

A Machine Learning-based Student Placement Prediction System that predicts whether a student is likely to be **Placed** or **Not Placed** using academic performance, technical skills, career preparation, and other student-related characteristics.

## 📌 Project Overview

The project analyzes student-related data and applies multiple Machine Learning classification algorithms to predict placement outcomes.

The system includes:

- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Correlation analysis
- Categorical feature encoding
- Feature scaling
- Multiple Machine Learning models
- Model evaluation and comparison
- Confusion matrix analysis
- Random Forest feature importance
- Model improvement
- Hyperparameter tuning
- Placement probability prediction
- Student risk analysis

The dataset contains **100,000 student records and 26 columns**.

## 🎯 Objective

The main objective is to develop a predictive system that can estimate whether a student is likely to be placed based on factors such as:

- Academic performance
- Technical skills
- Communication skills
- Internships
- Projects
- Certifications
- Interview performance
- Extracurricular activities
- Leadership activities
- Other student-related characteristics

The system can also help identify students who may need additional placement preparation.

## 📊 Dataset

The dataset contains information related to students' academic performance, skills, career preparation, and placement outcomes.

### Target Variable

`placement_status`

- `0` → Not Placed
- `1` → Placed

### Important Features

Some of the features used include:

- CGPA
- Internships
- Projects
- Certifications
- Coding Skill Score
- Aptitude Score
- Communication Skill Score
- Logical Reasoning Score
- Mock Interview Score
- Attendance
- Backlogs
- College Tier
- Branch
- Hackathons
- GitHub Repositories
- Leadership
- Volunteer Experience
- Study Hours

`student_id` was excluded because it is only an identifier.

`salary_package_lpa` was also excluded because salary information becomes available after placement and could cause **data leakage**.

## 🔍 Exploratory Data Analysis

EDA was performed to understand relationships between placement outcomes and student characteristics.

The analysis showed that placed students generally had slightly higher values for:

- Internships
- Projects
- Coding skill
- Aptitude
- Communication
- Logical reasoning
- Mock interview performance

Placed students also generally had fewer backlogs.

Some academic and extracurricular features such as CGPA, attendance, certifications, hackathons, GitHub repositories, and leadership showed smaller differences between the two placement groups.

## 📈 Correlation Analysis

Correlation analysis was performed on numerical features.

The strongest absolute correlation with placement status was observed for **backlogs (-0.0824)**.

Other notable correlations included:

| Feature | Correlation |
|---|---:|
| Internships | 0.0635 |
| Projects | 0.0610 |
| Coding Skill | 0.0508 |
| Mock Interview | 0.0461 |
| Logical Reasoning | 0.0363 |
| Communication | 0.0322 |
| Aptitude | 0.0317 |
| Leadership | 0.0222 |
| CGPA | 0.0121 |
| Attendance | -0.0084 |

The correlations were generally weak, so correlation was not interpreted as proof of causation.

## 🤖 Machine Learning Models

Four major classification algorithms were implemented as required:

1. **Logistic Regression**
2. **Random Forest**
3. **Support Vector Machine (SVM)**
4. **K-Nearest Neighbors (KNN)**

An additional **Decision Tree** model was also evaluated for comparison.

### Data Split

The dataset was divided into:

- **80% Training Data**
- **20% Testing Data**

with `random_state = 42` and class proportions preserved.

### Feature Scaling

Feature scaling was applied because some algorithms are sensitive to differences in feature ranges.

Scaling is particularly important for:

- Logistic Regression
- SVM
- KNN

Tree-based models such as Random Forest are less sensitive to feature scaling.

## 📊 Model Performance

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | 57.01% | 57.89% | 77.24% | 66.18% |
| Decision Tree | 50.59% | 54.73% | 53.67% | 54.15% |
| Random Forest | 55.27% | 57.08% | 71.96% | 63.66% |
| SVM | 56.97% | 57.85% | 77.31% | 66.18% |
| KNN | 52.12% | 55.62% | 59.72% | 57.60% |
| Improved Random Forest | 56.72% | 57.07% | 82.82% | 67.58% |
| **Tuned Random Forest** | **56.44%** | **56.51%** | **86.82%** | **68.47%** |

The **Tuned Random Forest** achieved the highest F1-score among the evaluated models.

## 🌲 Feature Importance

Random Forest feature importance was used to identify influential features.

The most important features included:

- Mock Interview Score
- Coding Skill Score
- Aptitude Score
- Logical Reasoning Score
- Communication Skill Score
- Leadership Score
- Extracurricular Score
- LinkedIn Connections
- CGPA
- Attendance

These findings were compared with the patterns observed during EDA.

## ⚙️ Hyperparameter Tuning

`RandomizedSearchCV` was used to tune the Random Forest model.

### Best Parameters

```text
n_estimators = 400
max_depth = 10
min_samples_split = 15
min_samples_leaf = 2
max_features = sqrt
