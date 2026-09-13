<div align="center">

# 📱 Google Play Store Analysis

### 📊 Exploratory Data Analysis & User Review Sentiment Analysis

**OASIS INFOBYTE INTERNSHIP — LEVEL 2 | PROJECT 4**

[![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge\&logo=python)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge\&logo=jupyter)](https://jupyter.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458?style=for-the-badge\&logo=pandas)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Numerical_Computing-013243?style=for-the-badge\&logo=numpy)](https://numpy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0?style=for-the-badge)](https://seaborn.pydata.org/)
[![Plotly](https://img.shields.io/badge/Plotly-Interactive_Charts-3F4F75?style=for-the-badge\&logo=plotly)](https://plotly.com/)
[![NLTK](https://img.shields.io/badge/NLTK-Sentiment_Analysis-85A0A6?style=for-the-badge)](https://www.nltk.org/)

</div>

---

## 📌 Project Overview

**Google Play Store Analysis** is a Python-based exploratory data analysis project developed as part of the **OASIS INFOBYTE Internship — Level 2, Project 4**.

The project analyzes Android application data and user reviews to explore patterns related to:

* 📱 App categories
* ⭐ App ratings
* 📈 Reviews
* 📥 Install counts
* 💰 Free and paid applications
* 💵 App pricing
* 👥 Content ratings
* 📝 User reviews
* 😊 User sentiment

The project combines **data cleaning, exploratory data analysis, visualization, and sentiment analysis** to investigate characteristics of applications available on the Google Play Store.

---

# 🎯 Objectives

The major objectives of the project are:

* 📊 Explore the distribution of applications across different categories.
* ⭐ Analyze the distribution of application ratings.
* 📈 Examine application review counts.
* 📥 Investigate installation patterns.
* 💰 Explore pricing and free-versus-paid applications.
* 📱 Analyze application metadata.
* 📝 Examine user review data.
* 😊 Perform sentiment analysis on user reviews.
* 📊 Visualize analytical findings using multiple Python visualization libraries.
* 🧹 Practice real-world data cleaning and missing-value handling.

---

# 🗂️ Datasets

The project works with **two CSV datasets**.

## 1️⃣ `apps.csv`

The application dataset contains information such as:

| Column           | Description                 |
| ---------------- | --------------------------- |
| `App`            | Application name            |
| `Category`       | Application category        |
| `Rating`         | Average application rating  |
| `Reviews`        | Number of reviews           |
| `Size`           | Application size            |
| `Installs`       | Number of installations     |
| `Type`           | Free or Paid                |
| `Price`          | Application price           |
| `Content Rating` | Intended audience           |
| `Genres`         | Application genre           |
| `Last Updated`   | Last update date            |
| `Current Ver`    | Current application version |
| `Android Ver`    | Minimum Android version     |

---

## 2️⃣ `user_reviews.csv`

The review dataset contains user feedback and sentiment-related information.

Important columns include:

| Column                   | Description              |
| ------------------------ | ------------------------ |
| `App`                    | Application name         |
| `Translated_Review`      | User review text         |
| `Sentiment`              | Existing sentiment label |
| `Sentiment_Polarity`     | Sentiment polarity       |
| `Sentiment_Subjectivity` | Subjectivity score       |

---

# 🔄 Project Workflow

```text
                 ┌──────────────────────┐
                 │   Google Play Data   │
                 └──────────┬───────────┘
                            │
             ┌──────────────┴──────────────┐
             │                             │
             ▼                             ▼
       ┌─────────────┐              ┌─────────────┐
       │  apps.csv   │              │user_reviews │
       └──────┬──────┘              └──────┬──────┘
              │                            │
              ▼                            ▼
       Data Cleaning                Review Processing
              │                            │
              ▼                            ▼
       Exploratory Analysis          VADER Analysis
              │                            │
              ▼                            ▼
       Ratings / Categories          Positive / Neutral /
       Reviews / Installs            Negative Sentiment
              │                            │
              └────────────┬───────────────┘
                           ▼
                    Visualization
                           │
                           ▼
                  Analytical Insights
```

---

# 🛠️ Technologies Used

| Technology              | Purpose                       |
| ----------------------- | ----------------------------- |
| 🐍 **Python**           | Core programming language     |
| 📓 **Jupyter Notebook** | Development environment       |
| 🐼 **Pandas**           | Data loading and manipulation |
| 🔢 **NumPy**            | Numerical operations          |
| 📊 **Matplotlib**       | Data visualization            |
| 📈 **Seaborn**          | Statistical visualization     |
| 📉 **Plotly**           | Interactive visualization     |
| 🧠 **NLTK**             | Natural Language Processing   |
| 😊 **VADER**            | Sentiment analysis            |

---

# 📥 1. Data Loading

The notebook loads both datasets using Pandas:

```python
apps_df = pd.read_csv(apps_file_path)
user_reviews_df = pd.read_csv(user_reviews_file_path)
```

The initial inspection confirms that the application dataset contains fields including:

```text
App
Category
Rating
Reviews
Size
Installs
Type
Price
Content Rating
Genres
Last Updated
Current Ver
Android Ver
```

The review dataset contains:

```text
App
Translated_Review
Sentiment
Sentiment_Polarity
Sentiment_Subjectivity
```

---

# 🧹 2. Data Preparation

The notebook investigates missing and inconsistent values, particularly in the `Size` column.

Initially, values such as:

```text
Varies with device
```

are identified as non-numeric values.

The project attempts to convert:

```text
M → Megabytes
k → Kilobytes
G → Gigabytes
```

into numeric MB values.

---

# ⚠️ Size Column Cleaning Issue

An important result of the cleaning process is that the original `Size` column became entirely missing after the first replacement operation.

The notebook reports:

```text
Missing values in 'Size': 8196
```

and subsequently:

```text
Missing values in 'Size_MB': 8196
```

As a result, attempting to remove rows with missing `Size_MB` values produces:

```text
Number of apps after cleaning: 0
```

This is explicitly documented as a **data-cleaning limitation** rather than being presented as a successful transformation.

The notebook subsequently investigates the issue step-by-step by checking:

* Missing values
* Data types
* Column contents
* Rows affected by cleaning
* Results of `dropna()`

This demonstrates an important aspect of practical data analysis: **cleaning operations can themselves introduce or propagate missing data if the original representation is not handled correctly.**

---

# 📊 3. Category Exploration

The project analyzes the number of applications belonging to each Play Store category.

The analysis uses:

```python
category_counts = apps_df['Category'].value_counts()
```

and visualizes the resulting distribution using Seaborn.

### Visualization

```text
Number of Apps by Category
```

This allows the project to examine which application categories contain the largest number of entries in the dataset.

---

# ⭐ 4. Rating Analysis

The notebook investigates the distribution of application ratings using a histogram with KDE.

```python
sns.histplot(
    apps_df['Rating'],
    bins=20,
    kde=True
)
```

The cleaned rating statistics reported by the notebook are:

| Statistic          |  Value |
| ------------------ | -----: |
| Count              |  8,196 |
| Mean               | 4.1732 |
| Standard Deviation | 0.5366 |
| Minimum            |    1.0 |
| 25th Percentile    |    4.0 |
| Median             |    4.3 |
| 75th Percentile    |    4.5 |
| Maximum            |    5.0 |

### Key observation

The available application records have an overall average rating of approximately **4.17**, with the median at **4.3**.

This indicates that the ratings in the analyzed dataset are generally concentrated toward the higher end of the 1–5 rating scale.

---

# 📝 5. User Review Analysis

The second major component of the project focuses on user reviews.

The notebook examines the:

```text
Translated_Review
```

column and checks for missing values before performing sentiment analysis.

The project uses **NLTK's VADER SentimentIntensityAnalyzer**.

---

# 😊 6. Sentiment Analysis

VADER is initialized using:

```python
sia = SentimentIntensityAnalyzer()
```

The notebook calculates a compound sentiment score for each review:

```python
user_reviews_df['compound'] = (
    user_reviews_df['Translated_Review']
    .apply(
        lambda x:
        sia.polarity_scores(x)['compound']
    )
)
```

The compound score is then converted into three sentiment classes:

```text
Compound Score ≥ 0.05
        ↓
    Positive

Compound Score ≤ -0.05
        ↓
    Negative

Otherwise
        ↓
    Neutral
```

The classification logic is:

```python
user_reviews_df['sentiment'] = (
    user_reviews_df['compound']
    .apply(
        lambda x:
        'positive' if x >= 0.05
        else (
            'negative'
            if x <= -0.05
            else 'neutral'
        )
    )
)
```

---

# 📊 7. Sentiment Distribution

The project calculates:

```python
sentiment_counts = (
    user_reviews_df['sentiment']
    .value_counts()
)
```

and visualizes the resulting sentiment distribution using Seaborn.

### Analytical Flow

```text
User Review
     │
     ▼
VADER Sentiment Analyzer
     │
     ▼
Compound Sentiment Score
     │
     ├───────────────┐
     │               │
     ▼               ▼
Positive / Neutral / Negative
     │
     ▼
Sentiment Distribution
     │
     ▼
Visualization
```

This provides a straightforward way to understand the overall emotional orientation of the analyzed user-review corpus.

---

# 📈 Visualizations

The notebook uses several visualization tools.

### 📊 Seaborn

Used for:

* Category distribution
* Rating distribution
* Sentiment distribution

### 📉 Matplotlib

Used for:

* Histograms
* Bar charts
* Figure formatting
* Titles and axis labels

### 📊 Plotly

Imported for interactive visualization and can support further exploratory analysis.

---

# 🔍 Analysis Areas

The notebook establishes an analytical framework around several important Play Store metrics:

```text
                    Google Play Store
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
        ▼                  ▼                  ▼
     Category           Ratings            Reviews
        │                  │                  │
        ▼                  ▼                  ▼
  App Distribution    Rating Pattern     User Feedback
        │                  │                  │
        └──────────────────┼──────────────────┘
                           │
                           ▼
                    Sentiment Analysis
                           │
                           ▼
                 Positive / Neutral /
                     Negative
```

---

# 🧪 Data-Cleaning Experiments

One of the useful aspects of this notebook is that it does not simply perform a single cleaning operation and move on.

It investigates the effect of different operations, including:

* Replacing invalid values
* Converting data types
* Handling `NaN`
* Using `dropna()`
* Checking column-level missing values
* Testing individual cleaning steps
* Verifying the resulting DataFrame

For example:

```python
print(apps_df.isna().sum())
```

reveals the state of missing data across the dataset.

This makes the notebook useful for understanding **real-world exploratory data analysis and debugging of preprocessing pipelines**.

---

# 📁 Repository Structure

```text
OIBSIP-Intern-Saswati-Google-Play-Store-Analysis
│
├── ANDROID.ipynb
│
├── apps.csv
│
├── user_reviews.csv
│
└── README.md
```

### `ANDROID.ipynb`

Main Jupyter Notebook containing:

* Library installation
* Data loading
* Data inspection
* Data preparation
* Category analysis
* Rating analysis
* Missing-value investigation
* Sentiment analysis
* Visualization

### `apps.csv`

Google Play Store application dataset.

### `user_reviews.csv`

User review and sentiment dataset.

---

# 🚀 Getting Started

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/SASWATIMATHAN/OIBSIP-Intern-Saswati-Google-Play-Store-Analysis-PROJECT-4-LEVEL-2.git
```

```bash
cd OIBSIP-Intern-Saswati-Google-Play-Store-Analysis-PROJECT-4-LEVEL-2
```

---

## 2️⃣ Install Dependencies

```bash
pip install pandas matplotlib seaborn plotly nltk
```

---

## 3️⃣ Download the VADER Lexicon

Run inside Python/Jupyter:

```python
import nltk

nltk.download('vader_lexicon')
```

---

## 4️⃣ Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
ANDROID.ipynb
```

and execute the notebook cells sequentially.

---

# 📚 Key Learning Outcomes

Through this project, the following concepts were explored.

### 🐍 Python

* Functions
* Conditional logic
* Data processing
* File handling
* DataFrame operations

### 🐼 Data Analysis

* CSV data loading
* Data inspection
* Missing-value analysis
* Data cleaning
* Data type conversion
* Descriptive statistics

### 📊 Exploratory Data Analysis

* Category distributions
* Rating distributions
* Review analysis
* Dataset statistics

### 🧠 Natural Language Processing

* Review text processing
* VADER sentiment analysis
* Compound sentiment scoring
* Sentiment classification

### 📈 Visualization

* Bar charts
* Histograms
* KDE plots
* Sentiment distribution plots
* Interactive visualization with Plotly

---

# ⚠️ Project Limitations

The notebook contains several experimental data-cleaning steps, particularly around the `Size` field.

### `Size` Data

The supplied dataset representation resulted in the `Size` field becoming completely missing during the demonstrated preprocessing path.

Consequently:

```text
Size_MB → 0 valid observations
```

and:

```text
dropna(subset=['Size_MB', 'Rating'])
```

produced an empty DataFrame.

Therefore, the `Size` analysis should **not** be interpreted as a completed analysis of application sizes.

### Sentiment Analysis

The notebook performs a separate VADER-based sentiment analysis on user reviews. This should be viewed as an exploratory sentiment classification rather than a custom-trained NLP model.

### Dataset Scope

The project is based on the supplied historical Google Play Store datasets and therefore reflects the data contained in those files rather than current Google Play Store statistics.

---

# 🔮 Future Improvements

The project could be extended with:

### 📱 Application Analysis

* Top applications by installs
* Most-reviewed applications
* Highest-rated applications
* Free vs paid application comparison
* Price distribution
* Category-wise rating comparison
* Category-wise installation analysis

### 📊 Statistical Analysis

* Correlation between reviews and installs
* Relationship between ratings and reviews
* Category-level statistical summaries
* Outlier detection

### 😊 Advanced Sentiment Analysis

* Sentiment by application category
* Sentiment by individual application
* Polarity distribution
* Subjectivity analysis
* Comparison between existing sentiment labels and VADER predictions

### 📈 Interactive Dashboard

A future version could use:

```text
Plotly
   +
Streamlit
   ↓
Interactive Google Play Store Dashboard
```

with filters for:

* Category
* Rating
* Installs
* Price
* Type
* Content Rating
* Sentiment

---

# 🏆 Project Significance

This project demonstrates a practical **data-analysis workflow using a real-world application dataset**.

The project progresses through:

```text
Raw Data
   ↓
Data Inspection
   ↓
Data Cleaning
   ↓
Exploratory Analysis
   ↓
Visualization
   ↓
User Review Processing
   ↓
Sentiment Analysis
   ↓
Analytical Interpretation
```

The combination of application metadata and user-review data provides two complementary perspectives:

```text
APPLICATION SIDE
      │
      ├── Category
      ├── Rating
      ├── Reviews
      ├── Installs
      ├── Price
      └── Metadata
             │
             ▼
       Play Store Analysis
             ▲
             │
      USER SIDE
      │
      ├── Review Text
      ├── Sentiment
      ├── Polarity
      └── Subjectivity
```

---

# 🎓 Internship Context

**Program:** OASIS INFOBYTE Internship

**Level:** Level 2

**Project:** Project 4 — Google Play Store Analysis

**Primary Language:** Python

**Development Environment:** Jupyter Notebook

**Project Areas:** Data Analysis • Data Visualization • NLP • Sentiment Analysis

---

# 👩‍💻 Author

### **Saswati Anupama Mathan**

**M.Tech — Electronics & Communication Engineering (Specialisation - Communication)**

GitHub: `SASWATIMATHAN`

---

# 🙏 Acknowledgements

Special thanks to **OASIS INFOBYTE** for providing the internship opportunity and project framework through which this exploratory data analysis, visualization, and sentiment-analysis project was developed.

---

<div align="center">

### ⭐ If you find this project useful, consider giving the repository a star!

**Built with Python • Pandas • Seaborn • Matplotlib • Plotly • NLTK**

</div>
