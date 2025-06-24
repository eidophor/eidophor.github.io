---
title: "[MGT4516] AI Marketing Individual Presentations"
excerpt: "A series of Data Science analytics projects using Kaggle datasets<br/>: From Diabetes Classification to Recommendation Systems."
semester: "Fall-2024"
semester_sort: 202402
collection: portfolio
---

## 📝 Project Overview

This portfolio includes a series of **classic** data science projects developed as part of [**MKT4516 (AI Marketing)**] course.  
Each project used real-world Kaggle datasets, focusing on applying models to consumer data, classification, clustering, and recommender systems.  
The projects involved both **model development** and **interpretation** for marketing decision support.

## 🔬 Project Highlights
### 1. Diabetes Classification using SMOTE + Classification Models (코딩과제1)

- **Goal**: Predict whether a patient has diabetes using clinical data from the Pima Indian dataset.
- **Dataset**: `data-Lab-2-5-diabet.csv` — 800 samples with 9 clinical features.
- **Preprocessing**:
  - **SMOTE** (Synthetic Minority Over-sampling Technique) to address class imbalance (422 positives vs. 223 negatives).
  - **Train-Test Split**: 85% training / 15% test set with `random_state=42`.
  - **Feature Scaling**: `MinMaxScaler` for normalization.

- **Models Used**:
  - `Logistic Regression`
  - `SVM (Support Vector Machine)`
  - `Random Forest`
  - `XGBoost Classifier`

- **Evaluation Metrics**:
  - Accuracy, Recall, Confusion Matrix (focus on medical diagnostics: recall is prioritized).
  - Visualization with `Seaborn` heatmaps.

- **Insights**:
  - SVM showed the best performance at both recall and accuracy, particularly important in medical scenarios.
  - For relatively simple classification which has structural format, classic **support vector machine** and **Logistic Regression** are still good. <br/> Using these models, there is a huge advantage that we could interpret the results. 
  - SMOTE helped significantly reduce underfitting on minority class.

📄 [Download: Diabetes Classification Report (Korean)](/files/코딩과제1_김지수.pdf)

---

### 2. CNN Ensemble Model using MNIST Dataset (코딩과제2)
- **Goal**: Build a high-accuracy classification model using ensemble learning on the MNIST handwritten digits dataset.
- **Method**:  
  - Implemented 7 distinct CNN models using TensorFlow and Keras.  
  - Applied **data augmentation** (rotation, zoom, shift) to increase training robustness.  
  - Used **softmax probability averaging** (soft voting) to ensemble the predictions.  
  - Each CNN consisted of convolutional layers, batch normalization, dropout regularization, and dense output layers.  

- **Insights**:  
  - Individual CNNs achieved ~99.6% accuracy; the final **ensemble model reached 99.72% accuracy**.  
  - Ensemble reduced overfitting and improved generalization.  
  - Demonstrated the trade-off between model complexity and performance gain. We should choose the model considering the trade-off. 
  - Emphasized importance of batch normalization and dropout for stabilizing training.

📄 [Download: CNN Ensemble Report (Korean)](/files/코딩과제2_김지수.pdf)

---

### 3. Emotion Recognition via CNN (코딩과제3)

- **Dataset**: [FER2013 - Facial Expression Recognition](https://www.kaggle.com/datasets/msambare/fer2013)  
  48×48 grayscale facial images labeled across 7 emotion categories (Angry, Disgust, Fear, Happy, Sad, Surprise, Neutral)  
  ~28,000 training images / ~3,500 testing images

- **Model**: Custom CNN  
  Composed of 4 convolutional blocks with batch normalization and dropout layers, followed by fully connected layers.  
  Trained using **Adam optimizer (lr = 0.0001)** and categorical cross-entropy loss.

- **Preprocessing & Augmentation**:  
  - Image rescaling (`rescale=1./255`)  
  - Data augmentation with **horizontal flip**, **10% width/height shifts**
  - Train/Test Dataset split
  - 20% of training data used as validation set

- **Results**:  
  - **Training Accuracy**: ~72.08%  
  - **Validation Accuracy**: ~64.98%  
  - **The model was also tested on cartoon characters (e.g., Luffy) to explore whether it could be generalized to entirely different facial domains—reflecting the growing need for emotion recognition models to perform robustly across diverse visual contexts.**

- **Insights**:  
  - Performance was limited by the quality and quantity of the dataset.
  - Pretrained models (e.g., ResNet50/101) showed comparable accuracy but required significantly longer training time (~4–5 hours).
  - Highlighted the importance of data diversity in facial expression recognition tasks.
  - I referenced the code of a Kaggle Grandmaster, and found it unusual that they did not use a separate test set—only the training and validation sets were utilized. Later, I asked a professor of machine learning about this, and learned that in some cases—such as when writing a paper or when the dataset is sufficiently large—this approach can be acceptable. Although not theoretically proven, the professor mentioned that some papers have addressed this practice based on empirical grounds.
  
📄 [Download: Emotion CNN Report (Korean)](/files/코딩과제3_김지수.pdf)

---

### 4. Movie Recommendation System (코딩과제4)
- **Dataset**: [TMDB Movie Metadata](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata), containing ~5,000 movies with features such as title, cast, genres, keywords, overview, and popularity.
- **Models Used**:
  - *Content-Based Filtering*: Used TF-IDF to vectorize movie plot summaries (overview), and computed cosine similarity to recommend similar movies.
  - *Metadata-Based Filtering*: Extracted top actors, director, genres, and keywords to build a "metadata soup", vectorized using `CountVectorizer`, and applied cosine similarity.
- **Preprocessing**:
  - Filled missing overview entries, parsed JSON-like strings into Python lists/objects.
  - Cleaned and normalized text (lowercased, removed whitespace).
- **Implementation**:
  - Cosine similarity calculated on both TF-IDF and CountVectorizer matrices.
  - Created a `get_recommendations(title)` function that returns top 10 similar movies.
- **Insights**:
  - Older algorithmic approaches like TF-IDF-based similarity still perform reasonably well.
  - Recommendation quality depends on the relevance and richness of features used.
  - **Even simple "Top 10" rankings** (e.g., genre-wise popular items) can be effective in practical applications like Netflix.

📄 [Download: Recommender System Report (Korean)](/files/코딩과제7_김지수.pdf)

---

## 🎓 Learning Outcome
These machine learning projects demonstrate how fundamental models—from classification to recommendation—can enhance consumer insight and decision support in AI marketing.
They highlight the importance of data preprocessing, model interpretability, and ensemble strategies to boost performance and generalizability.
Overall, these projects emphasize that even classical models(in some cases, statistics by themselves are enough), when carefully applied, offer strong implications for real-world marketing applications.
