
# Fake News Classifier

## Project Overview

The **Fake News Classifier** is a machine learning web application built using Python and Streamlit. It analyzes a news headline and/or article text and predicts whether the supplied text belongs to the **FAKE** or **REAL** news class.

The application uses a trained Logistic Regression model and TF-IDF vectorization to convert text into numerical features for classification.

**Note:** This application performs statistical text classification. It does not independently verify news claims against trusted external sources.

## Features

- Enter a news headline and/or article text.
- Preprocess text using tokenization, stopword removal, and lemmatization.
- Convert text into numerical features using TF-IDF.
- Classify news text as FAKE or REAL.
- Display model confidence and estimated probabilities for both classes.
- Provide an interactive interface using Streamlit.
- Load the trained model and vectorizer from saved Joblib files.

## Technologies Used

- Python
- Streamlit
- Pandas and NumPy (if used in the training workflow)
- Scikit-learn
- NLTK
- TF-IDF Vectorizer
- Logistic Regression
- Joblib

## Machine Learning Approach

### 1. Text Preprocessing

The application prepares the input text using the following steps:

- Convert text to lowercase.
- Remove non-alphabetic characters.
- Normalize extra whitespace.
- Remove selected news datelines.
- Tokenize text into individual words.
- Remove English stopwords and selected news-source terms.
- Apply lemmatization to reduce words to their base forms.

### 2. Feature Extraction

**TF-IDF (Term Frequency–Inverse Document Frequency)** converts the processed text into numerical features based on the importance of terms.

The model configuration described in the application is:

- **Feature extraction:** TF-IDF
- **N-grams:** Unigrams and bigrams
- **Vocabulary size:** 5,000 terms

The saved vectorizer must use the same configuration and vocabulary as the one used during model training.

### 3. Classification

**Logistic Regression** predicts whether the input text belongs to one of the two classes.

| Encoded Class | Prediction |
|---|---|
| 0 | FAKE |
| 1 | REAL |

The application also displays the model's estimated probability for each class and the confidence associated with the predicted class.

## Application Workflow

1. User enters a news headline or article.
2. The application preprocesses the text.
3. The TF-IDF vectorizer transforms the text into numerical features.
4. The trained Logistic Regression model predicts the class.
5. The application displays the prediction and class probabilities.

## Project Structure

```text
Fake-News-Classifier/
│
├── app.py
├── fake_news_lr_model.joblib
├── fake_news_tfidf_vectorizer.joblib
├── requirements.txt
└── README.md
```

The Python filename can be changed, but the deployment command must match it. The two Joblib files should be placed beside the application file.

## Installation and Setup

### 1. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd Fake-News-Classifier
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with your actual GitHub repository URL.

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the Application

If the main file is named `app.py`, run:

```bash
streamlit run app.py
```

If the file has a different name, replace `app.py` with that filename.

## Requirements

Create a `requirements.txt` file containing the libraries required by the application:

```text
streamlit
scikit-learn
joblib
nltk
```

You may pin compatible package versions for reproducible deployment. The NLTK resources used by the application are downloaded automatically when needed.

## Limitations

- Predictions depend on the training dataset and learned text patterns.
- The model may misclassify satire, opinion pieces, breaking news, or unfamiliar topics.
- Model confidence is not proof of factual accuracy.
- The application does not retrieve or cross-check external news sources.
- Performance depends on the quality, balance, and representativeness of the training data.

## Future Enhancements

- Evaluate the model using accuracy, precision, recall, and F1-score.
- Add a confusion matrix and classification report.
- Compare Logistic Regression with other classification algorithms.
- Integrate trusted sources for additional fact-checking support.
- Improve the user interface and display model evaluation metrics.

## Disclaimer

This project is intended for educational and informational purposes. Predictions should not be treated as definitive evidence that a news article is true or false. Verify important claims using multiple reliable sources.

## Author

**Ravali Tatikonda**

Machine Learning | Python | Natural Language Processing | Streamlit
