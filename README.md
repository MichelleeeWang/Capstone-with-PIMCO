

Data Folder : 
1.	directionality_dictionary_all_df.csv: The manually created dictionary

Notebook(s) for each part:

1.	Data Preprocessing:  data_wrangling.ipynb
a.	input：topic_tagged_data_set & topic_untagged_data_set
b.	output:
i.	processed data set
ii.	1-gram & 2-gram vectorized feature matrix ( in pickle file)

2.	Topic Classifier & Auxiliary Growth topic Classifier:  topic_classifier.ipynb 
a.	input: processed data set
b.	output:  
i.	tfidf_vec.pickle: tfidf transformed feature matrix
ii.	rf.pickle: random forest topic assign model
iii.	tfidf_vec_is_growth.pickle: tfidf transformed feature  matrix for training the  auxiliary growth topic classifier
iv.	logi_clf.pickle : logistic regression is_growth classifier
v.	sample.csv: the result of the topic classifier and the original data 

3.	Directionality Analyzing Algorithms: 
Baseline model:  Directionality_Analyzing_Algorithms_benchmark.ipynb 
a.	input: direction  tagged data (in file “manual_direction_eng_completed”)
b.	output: performance for different model showed in the notebook

4.	Get feature Contribution (model preparation) : feature_contribution_train.ipynb
a.	this part of the notebook is used for getting the features which contributes the most to the topic assignment of the sentence
b.	this is part of the preparation for directionality prediction model
c.	output: excel with the most important features, in file “feature_contribution_train”
d.	eg. [('labor', 0.36359374997240984), ('labor market', 0.25873850511490115)], ‘labor’’ contribution for the result in 0.36 among all the 1-gram and 2-gram features.

5.	Get word similarity to direction word(model preparation): word_similarity_train.ipynb
a.	this part of the notebook is used for getting the highlight direction word in the sentence, we get the direction word based on two algorithms, stem recognition and word similarity recognition
b.	output:
i.	excel with information of the direction word in the sentence and the corresponding	direction word in the dictionary as well as their similarity.
ii.	For each sentence, we return 7 lists (because there might be more than one direcitonality words in one sentence):
    list of indices of directionality words
    list of indices of corresponding dictionary words
    list of directionality words
    list of corresponding dictionary words
    list of similarities (between 0 and 1)
    list of number of negative words in front of the directionality words. We only consider two words preceding the directionality words.
    list of directionalities
    Directionality Analyzing Algorithms：
Unsupervised model:Directionality_Analyzing_Algorithms_unsupervised.ipynb 
a.	get the prediction of the directionality based on our unsupervised model.
b.	For each sentence we return 16 types of directionality score
c.	These scores are based on the combination of 2 distance types(absolute position and dependency parse tree shortese path(spacy)), 2 types of directionality word recognition(stem and similarity) and 4 types of aggregate methods(simple average, weighted by inverse of the distance, weighted by contribution, weighted by inverse of the distance and contribution)
d.	detailed result showed in the notebook
7.	Backtesting strategy:Portfolio backtesting.ipynb
a.	input: prediction result and the financial index to compare with
b.	output: simulation and evaluation of the performance of the portfolio.


![image](https://user-images.githubusercontent.com/52937467/175197549-9ccb368f-03a0-4ff5-86bc-bc726c5a25ba.png)
