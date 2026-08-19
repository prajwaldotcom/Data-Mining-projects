# 🎓 Smart Campus Analytics

## 📌 Project Overview

**Smart Campus Analytics** is a Data Mining project that analyzes student experience and satisfaction using survey data.

The system analyzes student ratings of different university facilities such as **classrooms, faculty, Wi-Fi, cafeteria, library, sports, clubs, technical events, cleanliness, safety, and transportation**.

The project applies Data Mining and Machine Learning techniques to:

* Clean and preprocess student survey data
* Analyze student satisfaction
* Calculate an overall **Happiness Index**
* Group students using **K-Means Clustering**
* Predict whether a student is **Satisfied or Not Satisfied**
* Identify important factors affecting satisfaction using a **Decision Tree**
* Generate interactive visualizations
* Provide campus improvement recommendations
* Provide an interactive **Gradio dashboard**

The project processes a survey containing **145 student responses and 18 columns**.

---

## 🎯 Objectives

The main objectives of this project are:

1. Analyze student satisfaction with university facilities.
2. Identify areas where students are satisfied or dissatisfied.
3. Calculate an overall student Happiness Index.
4. Divide students into satisfaction groups using K-Means clustering.
5. Predict student satisfaction using a Decision Tree classifier.
6. Identify the most influential satisfaction factors.
7. Compare satisfaction across different academic departments.
8. Generate practical recommendations for campus improvement.
9. Provide an interactive dashboard for data analysis.

---

## 📊 Dataset

The project uses a **Student Experience & Engagement Survey** stored in an Excel file.

### Dataset Information

* **Total Students:** 145
* **Total Columns:** 18
* **Data Format:** Excel (`.xlsx`)

The dataset contains information related to:

| Category           | Description                                  |
| ------------------ | -------------------------------------------- |
| Department         | Student's program/department                 |
| Semester           | Current semester                             |
| Classrooms         | Satisfaction with classroom facilities       |
| Faculty            | Faculty interaction and support              |
| Wi-Fi              | Campus Wi-Fi quality                         |
| Cafeteria          | Food, cleanliness and service                |
| Library            | Library facilities and resources             |
| Sports             | Sports facilities                            |
| Clubs              | Student clubs and extracurricular activities |
| Technical Events   | Workshops, seminars and hackathons           |
| Cleanliness        | Campus cleanliness                           |
| Safety             | Campus safety and security                   |
| Transport          | University transportation                    |
| Overall Experience | Overall university satisfaction              |

The notebook automatically identifies the department/program column and extracts **11 satisfaction features** for analysis.

---

## 🔄 Project Workflow

```text
Student Survey Data
        ↓
Data Loading
        ↓
Data Cleaning
        ↓
Feature Extraction
        ↓
Missing Value Handling
        ↓
Happiness Index Calculation
        ↓
Exploratory Data Analysis
        ↓
Feature Scaling
        ↓
K-Means Clustering
        ↓
Decision Tree Classification
        ↓
Feature Importance Analysis
        ↓
Interactive Dashboard
        ↓
Campus Improvement Recommendations
```

---

## 🧹 Data Preprocessing

The following preprocessing operations are performed:

### 1. Remove Empty Rows

Rows containing no data are removed.

### 2. Remove Empty Columns

Columns containing no data are removed.

### 3. Remove Duplicate Records

Duplicate survey responses are removed.

### 4. Clean Column Names

Extra spaces are removed from column names.

### 5. Handle Missing Values

Missing numerical values in the extracted features are replaced using the **median** value.

### 6. Feature Extraction

Eleven major satisfaction features are extracted:

```text
Classrooms
Faculty
Wi-Fi
Cafeteria
Library
Sports
Clubs
Tech Events
Cleanliness
Safety
Transport
```

## These preprocessing steps are implemented directly in the notebook.

# 📈 Happiness Index

An **Average Rating** is calculated using the 11 satisfaction features.

The rating is converted into a **Happiness Index from 0 to 100**.

### Categories

| Happiness Score | Category          |
| --------------: | ----------------- |
|          80–100 | Very Happy        |
|           60–79 | Happy             |
|           40–59 | Neutral           |
|        Below 40 | Needs Improvement |

The notebook calculates the Happiness Index from the average facility rating and assigns each student to one of these categories.

### Overall Results

The project obtained:

* **Students:** 145
* **Average Rating:** 3.60 / 5
* **Average Happiness:** 65.08 / 100

---

# 📊 Exploratory Data Analysis

The project analyzes the average satisfaction for different campus facilities.

A bar chart is used to compare facility satisfaction levels.

The observed average ratings range from approximately:

* **Wi-Fi:** 3.04
* **Clubs:** 3.46
* **Sports:** 3.47
* **Tech Events:** 3.63
* **Classrooms:** 3.64
* **Faculty:** 3.64
* **Cafeteria:** 3.67
* **Cleanliness:** 3.67
* **Transport:** 3.68
* **Library:** 3.81
* **Safety:** 3.92

This helps identify which facilities require greater attention.

---

# 🔵 K-Means Clustering

K-Means clustering is used to group students according to their satisfaction levels.

Before clustering, the features are standardized using `StandardScaler`.

```python
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

K-Means is configured with:

```text
Number of clusters = 3
Random state = 42
n_init = 10
```

The three groups are:

1. **Low Satisfaction**
2. **Moderate Satisfaction**
3. **High Satisfaction**

### Cluster Results

| Cluster               | Students |
| --------------------- | -------: |
| Moderate Satisfaction |       70 |
| High Satisfaction     |       59 |
| Low Satisfaction      |       16 |

The cluster names are assigned according to the average Happiness Index of each cluster.

---

# 🌳 Decision Tree Classification

A Decision Tree classifier is used to predict whether a student is:

```text
Satisfied
```

or

```text
Not Satisfied
```

The target variable is created using the Happiness Index:

```text
Happiness ≥ 60 → Satisfied
Happiness < 60 → Not Satisfied
```

The dataset is divided into:

* **80% Training Data**
* **20% Testing Data**

The Decision Tree uses:

```text
max_depth = 4
random_state = 42
```

### Model Accuracy

The Decision Tree achieved:

**93.10% Accuracy**

---

# ⭐ Feature Importance

The Decision Tree is also used to identify which features have the greatest influence on satisfaction.

### Feature Importance

| Feature     | Importance |
| ----------- | ---------: |
| Clubs       |   0.485482 |
| Cafeteria   |   0.178657 |
| Safety      |   0.096337 |
| Library     |   0.087380 |
| Transport   |   0.077304 |
| Classrooms  |   0.035389 |
| Faculty     |   0.027962 |
| Cleanliness |   0.011490 |
| Wi-Fi       |   0.000000 |
| Sports      |   0.000000 |
| Tech Events |   0.000000 |

According to the trained Decision Tree, **Clubs** has the highest feature importance, followed by **Cafeteria** and **Safety**.

---

# 🖥️ Interactive Dashboard

The project includes an interactive dashboard developed using **Gradio** and **Plotly**.

The dashboard provides several sections.

### 📊 1. Live Dashboard

Users can select a department and view:

* Number of students
* Average Rating
* Happiness Index
* Facility Satisfaction
* Student Happiness Distribution
* Department-wise Happiness
* Top Student Concerns
* Action Plan

The available departments include:

```text
B.Tech
BCA
BSc
M.Tech
MCA
MSc
```

---

### 👨‍🎓 2. Student Analysis

Users can enter ratings from **1 to 5** for:

* Classrooms
* Faculty
* Wi-Fi
* Cafeteria
* Library
* Sports
* Clubs
* Technical Events
* Cleanliness
* Safety
* Transportation

The system calculates:

* Average Rating
* Happiness Index
* Student Status
* Areas requiring improvement

The rating scale is:

```text
1 = Very Poor
2 = Poor
3 = Average
4 = Good
5 = Excellent
```

---

### 📋 3. Cleaned Data

The dashboard displays the cleaned survey data so that users can inspect the processed dataset.

---

### 🤖 4. Data Mining

This section displays:

* K-Means clustering results
* Three satisfaction groups
* Decision Tree prediction
* Decision Tree accuracy
* Feature importance

---

### 💡 5. Action Plan

The system generates recommendations based on student satisfaction ratings.

Examples include:

* Improve classroom facilities.
* Increase faculty interaction and mentoring.
* Improve Wi-Fi speed and coverage.
* Improve cafeteria quality and hygiene.
* Add library resources and study spaces.
* Improve sports facilities.
* Increase club activities.
* Conduct more technical events.
* Improve campus cleanliness.
* Improve security and emergency support.
* Improve transportation availability and routes.

---

# 🛠️ Technologies Used

### Programming Language

* Python

### Libraries

* Pandas
* NumPy
* Scikit-learn
* Plotly
* Gradio
* OpenPyXL

The notebook installs and imports these libraries for data processing, visualization, machine learning and dashboard development.

### Machine Learning Techniques

* K-Means Clustering
* Decision Tree Classification
* StandardScaler
* Train-Test Split
* Accuracy Evaluation
* Feature Importance

---

# 📁 Project Structure

```text
Smart-Campus-Analytics/
│
├── DM_finalproject(2).ipynb
├── Un Student Experience & Engagement Survey (Responses) (1).xlsx
└── README.md
```

---

# ▶️ How to Run the Project

## Step 1: Open Google Colab

Upload:

```text
DM_finalproject(2).ipynb
```

to Google Colab.

## Step 2: Upload Dataset

Upload the Excel survey dataset:

```text
Un Student Experience & Engagement Survey (Responses) (1).xlsx
```

Make sure the file path matches the path used in the notebook.

## Step 3: Install Required Libraries

Run:

```python
!pip install -q gradio openpyxl plotly scikit-learn
```

## Step 4: Run All Cells

Execute the notebook cells from top to bottom.

## Step 5: Launch Dashboard

The final cell launches the Gradio application:

```python
app.launch(share=True)
```

The notebook generates a temporary Gradio public URL when the application is launched.

---

# 📌 Key Results

| Metric                 |      Result |
| ---------------------- | ----------: |
| Total Students         |         145 |
| Total Dataset Columns  |          18 |
| Satisfaction Features  |          11 |
| Average Rating         |    3.60 / 5 |
| Average Happiness      | 65.08 / 100 |
| K-Means Clusters       |           3 |
| Low Satisfaction       |          16 |
| Moderate Satisfaction  |          70 |
| High Satisfaction      |          59 |
| Decision Tree Accuracy |      93.10% |

---

# 💡 Conclusion

The **Smart Campus Analytics** project demonstrates how Data Mining and Machine Learning can be applied to student survey data to understand university experience and satisfaction.

The analysis shows an overall average rating of **3.60/5** and an average Happiness Index of **65.08/100**. K-Means clustering divides students into **Low, Moderate, and High Satisfaction** groups, while the Decision Tree achieves **93.10% accuracy** in predicting student satisfaction.
The project can help university management identify areas requiring improvement and make data-driven decisions to improve the overall student experience.

---

# 🚀 Future Enhancements

Possible future improvements include:

* Add more student responses for better model generalization.
* Add additional machine learning algorithms.
* Compare multiple classification models.
* Add advanced statistical analysis.
* Include sentiment analysis of student comments.
* Add historical survey data for trend analysis.
* Deploy the application permanently.
* Add database integration.
* Add user authentication.
* Generate downloadable reports.

---

# 👨‍💻 Project Type

**Data Mining / Machine Learning / Student Analytics**

### Main Concepts Demonstrated

```text
Data Collection
       ↓
Data Preprocessing
       ↓
Exploratory Data Analysis
       ↓
Feature Engineering
       ↓
K-Means Clustering
       ↓
Decision Tree Classification
       ↓
Model Evaluation
       ↓
Interactive Visualization
       ↓
Recommendation System
```

---

## 📜 License

This project is created for **academic and educational purposes**.
