# Log-anomaly-detection
In computing, logging is the act of keeping a log of events that occur in a computer system, such as problems, errors or just information on current operations. These events may occur in the operating system or in other software. A message or log entry is recorded for each such event. Log Anomaly Detection is simply detecting anomalies in logs deposited by softwares using Machine Learning.

Anomaly is anything that is different from what is usually perceived as normal - an exception. In software engineering, anomaly can be defined as occurrence of rare or unexpected events that does not fit into the normal patterns and hence a suspicious one. Examples could be:

Unexpected failure of a service
Sudden increase/decrease of user activity in a customer facing system
Reasons for these anomalies could be different, like:
Entry of unperceived inputs to the system
System running out of memory
# Log Anomaly Detection

## 1. Data Input

The data is in JSON (JavaScript Object Notation) format, representing a Hash Table type table.

## 2. Pre-processing

### Tokenization

The text input was split into tokens, including numbers, dates, and code. Columns [0, 1, 2, 3, 9] were selected from the log data.

### Data Cleaning

The log data was cleaned, and irrelevant parts were removed, leaving only the information related to "KERNEL INFO instruction cache parity error corrected."

### Corpus and Vectorization

The log data was converted into a "bag of words" corpus, and then two vectorization techniques were applied:

1. **CountVectorizer:** It built a vocabulary of unique words and transformed the log data into a feature matrix representing word counts.

2. **TF-IDF Vectorizer:** It calculated term frequency-inverse document frequency (TF-IDF) scores for the words in the log data.

### Word Embeddings

Word embeddings using Jay Alammar's "Word2Vec" method were generated for the log data.

### Undersampling

Undersampling was performed to balance the dataset.

### Normalization

The data was normalized using the stemming method from NLTK. Words were truncated to their root form, such as "eating" to "eat," "corrected" to "correct," and "instruction" to "instruct."

### Lemmatization

Lemmatization was applied to further normalize the data by reducing words to their base form. For example, "better" was converted to "good."

### Stop Word Removal

Commonly occurring stop words like "is," "and," and "of" were removed from the data as they don't carry significant meaning.

## 3. Feature Extraction

The data was processed and prepared for feature extraction using CountVectorizer.

### Tokenization

The text documents were tokenized, splitting them into individual words or tokens.

### Vocabulary Building

CountVectorizer built a vocabulary, mapping each unique word (token) in the corpus to an index.

### Counting

For each document in the corpus, CountVectorizer counted the occurrences of each word in the vocabulary and represented them as feature vectors.


## 4. Model Training

After data normalization and feature extraction, the following machine learning models were trained:

1. Neural Networks
2. Decision Tree Classifier
3. K-Nearest Neighbors Classifier (KNN)
4. XGBoostClassifier

## 5. Model Evaluation

### Confusion Matrix

For each trained model, a confusion matrix was generated to evaluate its performance on the test data.

### Evaluation Metrics

The following evaluation metrics were computed for each model:

1. **Accuracy:** The proportion of correctly classified instances.
2. **Precision:** The proportion of true positive predictions among all positive predictions.
3. **Recall:** The proportion of true positive predictions among all actual positive instances.
4. **F-score:** The harmonic mean of precision and recall, providing a balanced measure of the two metrics.

## 6. Prediction

Finally, the trained XGBoostClassifier was used to predict on new data. The output was evaluated to identify anomalies or patterns.

