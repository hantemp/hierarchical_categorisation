# hierarchical_categorisation
Hierarchical categorisation of products based on text descriptions.

Dataset: 

Text descriptions of products have been provided ('Description'). Each product has been assigned to one high-level ('Level_1') category, one medium-level ('Level_2') category, and one specific ('Level_3') category. There is no overlap.

Process:

After EDA and data cleaning, text was processed and transformed to TF-IDF vectors using NLTK.

After model selection and optimisation based on cross-validation of the training set, a single multiclass classifier was trained to predict the level-1 class of the test set. The best results were achieved using sklearn's ComplementNB() classifier, with a range of ngrams from 1-4.

Multiple multiclass classifiers – one for each level-1 class in the training set – were trained on data from to predict the level-2 class, and the classifier to be used for prediction was based on level-1 prediction. 

The same approach was carried out for level-3 prediction: multiple multiclass classifiers – one for each level-2 class in the training set – were trained on data from to predict the level-3 class, and the classifier to be used for prediction was based on level-2 prediction. 

This approach improved accuracy significantly for the subclasses, compared to training a single multiclass classifier on the whole training set and using it to predict the whole test set. A downside of this approach is that items that are misclassified in the first round remain so.
