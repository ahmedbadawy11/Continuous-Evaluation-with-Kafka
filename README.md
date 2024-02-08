# Continuous-Evaluation-with-Kafka

## Introduction
This repository contains the code and documentation for a machine learning project focusing on the analysis and modeling of a static dataset, as well as the dynamic simulation of model behavior in real-time scenarios. The project aims to develop and compare machine learning models for cyber security attack detection, emphasizing both static and dynamic aspects.

## Static Part:

In the initial phase of this project, an in-depth analysis of the static dataset was conducted. The dataset, named static_dataset.csv, comprises 15 features and their corresponding labels, totaling 268,074 rows. Two of these features contain categorical values, necessitating specific preprocessing steps.

Exploratory data analysis involved generating histograms to visualize the distribution of feature values and assessing skewness. Additionally, outlier detection was executed using box plots. It was observed that the dataset exhibited minimal class imbalance, with Class 1 constituting 54.9% and Class 0 constituting 45.1%.

The data underwent a meticulous cleansing process, involving the removal of missing values and duplicate rows (91,803 instances). Categorical columns, 'sld' and 'longest_word,' were subjected to Target Encoding. The 'timestamp' column, deemed non-essential, was excluded from the dataset.

Feature selection techniques, including SelectKBest with Mutual Information, Chi-squared, and ANOVA, were employed to identify the most impactful features. The optimal number of features, determined to be 8, was selected for subsequent model training.

To assess model performance, the dataset was split into an 80% training set and a 20% test set. The F1-Score was chosen as the performance metric due to its suitability for imbalanced class distributions, crucial in the context of Cyber Security attacks.

Two prominent classification algorithms, Logistic Regression and Random Forest, were selected for model development. Both models were initially trained with the entire dataset and then subjected to feature selection. The Chi-squared method emerged as the optimal feature selector for both models, yielding F1-Scores of 80.439% and 80.37%, respectively.

![image](https://github.com/ahmedbadawy11/Continuous-Evaluation-with-Kafka/assets/59053820/22962c8c-e36b-47cd-b1a0-6ea25d2a2e07)


Hyperparameter tuning was performed on both models, leading to slight performance improvements. The Logistic Regression model achieved an F1-Score of 80.443%, while the Random Forest model attained 80.436%.

A comparative analysis revealed that the Logistic Regression model, especially after feature selection and hyperparameter tuning, outperformed the Random Forest model in terms of precision and recall balance. A final pipeline, comprising feature selection, scaling, and the Logistic Regression classifier, was created and saved for future use.

![image](https://github.com/ahmedbadawy11/Continuous-Evaluation-with-Kafka/assets/59053820/9f389a5d-ecd6-4ea4-b747-7fb85928d167)


## Dynamic Part:

The dynamic aspect of the project focused on simulating the model's behavior in real-time scenarios, particularly when faced with new data. A function was devised to read 1,000 datapoints from a streaming source and convert them into a format akin to the static data.

The dynamic model initially mirrored the static model but underwent a reevaluation process when the F1-Score fell below a predefined threshold (0.85). Data preprocessing steps were replicated from the static model, and a sample from the static data was utilized for retraining.

Streaming data was processed in batches of 1,000 rows, and both static and dynamic models were assessed using the F1-Score. When the dynamic model's F1-Score dipped below the threshold, a retraining process was triggered.

The F1-Scores of both models were visualized, highlighting the stability of the static model and the dynamic model's adaptability through retraining. The dynamic model demonstrated a slightly higher F1-Score range (82%-87%) compared to the static model (75%-87%), showcasing its effectiveness in evolving scenarios.

![image](https://github.com/ahmedbadawy11/Continuous-Evaluation-with-Kafka/assets/59053820/b02d236c-3e4e-43f1-9a6c-f12dc31c7ca6)

Advantages of the dynamic model included real-time adaptability and consistent performance with new data. However, limitations were acknowledged, such as potential scenarios where retraining might not lead to F1-Score improvement and scalability challenges with large volumes of streaming data.

Through this dynamic simulation, valuable insights were gained into deploying machine learning models in real-time scenarios, emphasizing the importance of stability and adaptability in dynamic environments.
