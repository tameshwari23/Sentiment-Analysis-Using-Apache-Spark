# Real-Time Social Media Sentiment Analysis Using Apache Spark

## 1. Project Overview

Real-Time Social Media Sentiment Analysis is a Big Data Analytics project that analyzes social media posts and classifies them as **Positive or Negative** using Machine Learning.

The project uses the Sentiment140 dataset, which contains approximately 1.6 million tweets. Apache Spark and PySpark are used to process the dataset efficiently, while a Machine Learning model learns to predict sentiment from tweet text.

New tweets are introduced in batches to simulate real-time processing. An analytics dashboard presents sentiment statistics and visualizations to help users understand public opinion.

## 2. Problem Statement

Social media platforms generate large volumes of text every day. Manually analyzing these posts to understand public opinion is time-consuming and difficult to scale.

This project aims to automate sentiment classification using Big Data processing and Machine Learning techniques, making it easier to analyze large collections of tweets and summarize public reactions.

## 3. Objectives

- Process a large social media dataset using Apache Spark.
- Clean and preprocess tweet text.
- Perform sentiment analysis using Machine Learning.
- Classify tweets as positive or negative.
- Simulate incoming tweets in batches.
- Display sentiment statistics and trends using charts.
- Evaluate the trained model using standard classification metrics.

## 4. Dataset

**Dataset:** Sentiment140

**Source:** [Sentiment140 on Kaggle](https://www.kaggle.com/datasets/kazanova/sentiment140)

The original training dataset contains approximately 1.6 million tweets with sentiment labels.

### Dataset Columns

| Column | Description |
|---|---|
| `sentiment` | Sentiment label: 0 = Negative, 4 = Positive |
| `tweet_id` | Unique tweet identifier |
| `date` | Date and time of the tweet |
| `query` | Search query metadata |
| `user` | Username associated with the tweet |
| `text` | Tweet text |

**Note:** The original dataset contains positive and negative labels, not a separate neutral class. The downloaded file should be verified before analysis.

## 5. Technologies Used

- **Python** — Main programming language.
- **Apache Spark** — Big Data processing engine.
- **PySpark** — Python interface for Apache Spark.
- **Spark MLlib** — Machine Learning pipeline and model training.
- **Pandas** — Data analysis and preparation for visualization.
- **Matplotlib / Plotly** — Charts and data visualization.
- **Google Colab** — Development and execution environment.

Hadoop HDFS can optionally be integrated if distributed storage is required by the lab.

## 6. System Workflow

1. **Data Collection:** Obtain historical tweets from Sentiment140.
2. **Data Loading:** Load the CSV dataset using PySpark.
3. **Data Preprocessing:** Handle malformed or missing records and clean tweet text.
4. **Feature Extraction:** Convert text into numerical features suitable for Machine Learning.
5. **Model Training:** Train a sentiment classification model using labeled tweets.
6. **Model Evaluation:** Evaluate performance using accuracy, precision, recall, and F1-score.
7. **Simulated Real-Time Processing:** Introduce new tweets in batches and classify them using the trained model.
8. **Dashboard:** Visualize sentiment counts, percentages, and trends.
9. **Export Results:** Save analyzed tweets and their predicted sentiment to a CSV file.

## 7. Main Features

- Large-scale tweet processing using PySpark.
- Automated positive and negative sentiment classification.
- Text preprocessing and feature extraction.
- Simulated incoming tweet batches.
- Sentiment distribution charts.
- Sentiment percentage calculations.
- Recent tweet analysis.
- Model performance evaluation.
- Exportable sentiment analysis results.

## 8. Installation and Setup

### Step 1: Open Google Colab

Visit [Google Colab](https://colab.research.google.com/) and create a new notebook.

### Step 2: Install PySpark

Run the following command in a notebook cell:

```python
!pip install -q pyspark
```

Install any additional visualization or machine-learning libraries required by your implementation.

### Step 3: Download the Dataset

Download Sentiment140 from Kaggle, extract the ZIP file, and upload the CSV file to Google Colab.

### Step 4: Initialize Spark

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("Sentiment140Analysis") \
    .master("local[*]") \
    .getOrCreate()

print("Spark started successfully!")
```

### Step 5: Load the Dataset

Define the six-column schema and load the CSV using PySpark. Ensure that the file path matches the uploaded dataset.

```python
file_path = "/content/training.1600000.processed.noemoticon.csv"

df = spark.read.csv(
    file_path,
    schema=schema,
    header=False,
    encoding="UTF-8"
)

df.show(5, truncate=False)
```

Here, `schema` should be defined according to the six columns described in the Dataset section.

## 9. Dashboard and Expected Output

The planned dashboard will display:

- Total number of tweets processed.
- Number of positive tweets.
- Number of negative tweets.
- Percentage distribution of sentiment.
- Bar chart showing sentiment counts.
- Pie chart showing sentiment percentages.
- Sentiment trends across incoming batches.
- Recent tweets with predicted sentiment.

The dashboard and model results will be documented after implementation and testing.

## 10. Evaluation Metrics

The Machine Learning model will be evaluated using:

- **Accuracy:** Overall proportion of correct predictions.
- **Precision:** Proportion of predicted positive or negative cases that are correct for the relevant class.
- **Recall:** Proportion of actual cases of a class that the model correctly identifies.
- **F1-score:** Harmonic mean of precision and recall.
- **Confusion Matrix:** Summary of correct and incorrect classifications.

Actual metric values will be added after model evaluation.

## 11. Applications

- Brand reputation monitoring.
- Customer feedback analysis.
- Product review analysis.
- Marketing campaign evaluation.
- Public opinion analysis.
- Identification of frequently mentioned customer complaints.

## 12. Limitations

- The original Sentiment140 dataset contains only positive and negative sentiment labels.
- Historical dataset analysis is not itself real-time processing.
- Simulated incoming batches demonstrate incremental processing but do not connect to a live social media API.
- Sentiment predictions can be affected by sarcasm, slang, spelling errors, and context.
- Google Colab local mode does not demonstrate a multi-node Spark cluster.

## 13. Future Scope

- Integrate an authorized live social media data source.
- Implement continuous ingestion using Spark Structured Streaming.
- Add neutral sentiment classification using a suitable labeled dataset.
- Develop an interactive web dashboard using Streamlit.
- Integrate Hadoop HDFS for distributed storage.
- Compare different Machine Learning models.
- Analyze sentiment for specific products, brands, or events.

## 14. Team Members

- Student 1: Add name and roll number.
- Student 2: Add name and roll number.

**Department:** Computer Science and Engineering (AI & Data Science)

**Institution:** Ramdeobaba University, Nagpur

**Subject:** Big Data Analytics Lab

## 15. Conclusion

This project demonstrates how Apache Spark and Machine Learning can be used to analyze large volumes of social media text. By processing labeled tweets, predicting sentiment, simulating incoming posts, and visualizing the results, the system provides a practical introduction to Big Data Analytics and sentiment classification.

The project can be extended in the future to support live data sources, continuous streaming, and more advanced sentiment analysis techniques.
