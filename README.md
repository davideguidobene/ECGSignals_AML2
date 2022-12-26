# ECGSignals_AML2
Project 2 for the course of Advanced Machine Learning. Heart rythm classification from manually perturbed ECG Signals. Evaluation is based on F1-score.

#RESULTS
35th team out of 132 teams. Score: 0.83 (1st team score: 0.87. Last team score: 0.25).

#REPORT
Preprocessing:
- every row of the dataset
   - is stripped of its missing value
   - the resulting signal is cleaned using the fuction ecg_clean of neurokit
   - using the function ecg_peaks of neurokit and delineate, the peaks are extracted from the signal
   - from the resulting preprocessed signal, the main features are extracted
- all the features are scaled appropriately using StandardScaler from sklearn

Classification:
- the classification task is done by an ensemble of 5 classification algorithms implemented through StackingClassifier from sklearn
- the ensembled algorithms are:
   - catboost (CatBoostClassifier from catboost with objective  &#39;MultiClass&#39;, 300 iterations, random_state=0, eval_metric &#39;TotalF1:average=Micro&#39;)
   - extratrees (ExtraTreesClassifier from sklearn with 1000 estimators)
   - support vector machine (SVC from sklearn with default parametheres)
   - xgboost (XGBClassifier from xgboost with 100 estimators, objective=&#34;multi:softmax&#34; and metric f1_score)
   - random forest (RandomForestClassifier from sklearn with 300 estimators)
