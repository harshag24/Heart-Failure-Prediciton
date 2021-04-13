# INTRODUCTION
</br>
Cardiovascular disease is the term for all sorts of diseases that have an effect on the heart or blood vessels, as well as coronary heart condition (clogged arteries), which may cause heart attacks, stroke, noninheritable heart defects and peripheral artery unwellness. CVDs are the number 1 cause of death globally. An estimated 17.9 million people died from CVDs in 2016, representing 31% of all global deaths. Of these deaths, 85% are due to heart attack and stroke . Estimates from the World Health Organization (WHO) show that by 2030, CVDs will be the main cause of death throughout India, accounting for more than 35% of all deaths. Moreover, more than 800,000 people die of cardiovascular disease every year in the United States. Heart Attack is a complex clinical syndrome that occurs due to the heart’s inability to pump an adequate supply of blood to the body. All major body functions are disrupted without sufficient blood flow. One suffers a heart attack when the flow of oxygen rich blood is restricted to a certain section of heart which causes lack of enough oxygen. During a coronary failure, plaque will rupture and spill cholesterol and different substances into the blood. A grume forms at the positioning of the rupture. If the clot is giant, it will block blood flow through the arterial blood vessel, starving the heart of chemical element and nutrients (ischemia) that causes the heart muscles to die.
</br>
</br>
Three sorts of arteria malady will result in a heart failure. These are: ST section elevation infarct (STEMI), Non-ST section elevation infarct (NSTEMI) and arteria spasm. STEMI attack happens once the arteria is totally blocked, preventing blood from reaching an outsized space of the center. NSTEMI heart attack occurs when the coronary artery is partially blocked and blood flow is severely restricted. Coronary artery spasm happens once the arteries connected to the heart contract, limiting blood flow to the heart. These diseases can be caused depending on various factors such as age, gender, high blood pressure, high cholesterol, obesity, diabetes, sedentary lifestyle etc.
In recent times, Computer-aided diagnosis using artificial intelligence-based solutions has become increasingly popular [5]. Machine learning-based algorithms have started to become the quality choice for medical data analysis and classifications because of the availability of a large amount of healthcare data. It is so because machine learning algorithms can easily identify meaningful trends and patterns in them and classify the data [6]. For example, in our case, we were able to draw inference from the results obtained by applying various ML algorithms that elderly people with high BP were most prone to heart failure. Similarly, it is being used to detect various diseases such as Kidney Failure, Ebola Outbreak, Covid-19 etc.
</br>
</br>
This paper proposes a Machine Learning based Ensemble Solution to predict the probability of having heart failure in the next ten years. We began by implementing various ML algorithms: Logistic Regression, Gaussian Naïve Bayes, KNN, Support Vector Machine, Decision Tree, Random Forest, Adaptive Boosting, Light Gradient Boosting Machine, XGBoost and CatBoost and then we created an ensemble model combining all these models which gave the best results and we achieved 87.5% recall and 96.4% precision on test data. Adding to this, we also performed extensive Exploratory Data Analysis and gained insights on the correlation of various factors with a heart attack.
</br>
</br>

# DATASET
</br>

In this paper, we used the dataset provide on Kaggle based on ongoing Framingham Heart Study (FHS) [Dataset Link](https://www.kaggle.com/amanajmera1/framingham-heart-study-dataset). This study is being conducted on residents of Framingham, Massachusetts. The dataset provides the patients’ information. It includes 4,238 records (3594 records for healthy class and 644 records for people at risk from CHD). We split the data in the train and test part by applying stratified split of 25% for test data. Hence our training set consists of 3178 records and the testing set consists of 1060 records. The purpose of the classification is to assess if the patient has a 10-year chance of potential coronary heart disease (CHD).
</br></br>

# METHODOLOGY
## Data Preprocessing
The data has a lot of missing values which can reduce the statistical power of the algorithms used and can cause biases in the estimates, leading to invalid conclusions. We found 645 missing values in the dataset. So, to deal with this problem, we tried many strategies like dropping the Null values, imputing them with median, imputing them with median and imputing the with a frequently occurring constant. We finally used the mean of the column to replace the null values for each respective column because it gave us the best values for the chosen evaluation metrics.</br>
We also scaled the data using sklearn’s StandardScaler. Standard Scaling removes the mean and scales each feature/variable to unit variance. This operation is performed feature-wise in an independent way. We used this to normalize our data.</br>

## Training and Testing models
In order to find the most efficient algorithm, we trained several models on the dataset using existing machine learning classification algorithms and then we devised an ensemble model using these algorithms. </br>
These classification methods were evaluated using the following performance metrics-</br>
1. Accuracy- It is the fraction of predictions our model got right i.e., the number of correct predictions out of all predictions.</br>
2. Recall- It is the proportion of actual positives that were classified correctly from all predictions.</br>
3. Precision- It is the proportion of actual positives out of all predicted positives.</br>
In the medical domain, a False positive (people with low or no risk of heart failure) is not as harmful as a False Negative (people with a high risk of heart failure but remain undetected). </br>
Hence, recall is the most important metric among these for us.</br>
We tested various algorithms ranging from basic classifiers like Logistic Regression to complex boosting and bagging algorithms like XGBoost. Table 2 lists all the classifiers we used with their accuracy and recall on test data.</br></br>
An ensemble is a machine learning model that combines the predictions from two or more models. An ensemble can make better predictions and achieve better performance than any single contributing model. It can reduce the spread or dispersion of the predictions and model performance, especially when data is imbalanced which is our case as well. It can help in dealing with both bias and variance - variance representing scattered results that are difficult to converge, and bias representing miscalibration or error in targeting necessary results.

| Sr. No.  | Classifier | Accuracy (%) | Recall (%) |
| ------------- | ------------- | ------------- | ------------- |
| 1  | AdaBoost  | 85.80  | 86.62  |
| 2  | CatBoost  | 85.80 | 86.41  |
| 3  | Decision Trees  | 84.40  | 86.23  |
| 4  | K-nearest neighbour (k=10)  | 85.80  | 86.22  |
| 5  | Logistic regression  | **86.40**  | 86.50  |
| 6  | Light GBM  | 85.60  | 85.56  |
| 7  | Gaussian Naïve Bayes  | 82.50  | **87.06**  |
| 8  | Random Forest  | 86.20  | 86.13  |
| 9  | Support Vector Machine  | 85.90  | 86.23  |
| 10  | XG Boost  | 86.10  | 86.53  |

</br>
So, we designed an ensemble model using all the classifiers mentioned in the table above, taking Gaussian Naïve Bayes classifier as the meta classifier because the model devised resulted in the highest recall. A meta classifier is simply a classifier that makes the final prediction among all the predictions by using those predictions as features. So, it takes classes predicted by various classifiers and picks the final one as the result.
</br></br>
Table below shows the final performance of our ensemble model on the test data. It achieved a Recall score of 87.5% which is better than all the single classifiers.
</br>

| Performance Metrics  | Value(%) | 
| ------------- | ------------- | 
| Training accuracy  | 87.80  |
| Testing accuracy  | 85.20  |
| Recall  | 87.50  |
| Precision  | 96.47  |
| F1-score  | 91.76  |
