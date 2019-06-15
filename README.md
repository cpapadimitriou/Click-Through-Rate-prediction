# Click Through Rate (CTR) prediction wit pySpark on Criteo's advertising data

## Background 

The following analysis is based on a Kaggle dataset from Criteo, an internet advertising company focused on retargeting. Criteo's goal is to increase online clickthrough rates among consumers who have previously visited an advertiser's website. This information will be used by Criteo to more efficiently provide the right ads to the right people. Optimizing the retargeting process not only helps advertisers become more efficient in terms of how they spend their dollars, but also it reduces clutter for consumers who do not want to be "followed" by ads for irrelevant products (or ones they may have already purchased!). Our goal is to create a model that will most accurately predict clickthroughs (label = 1); Due to binary categorical nature of the output label (0,1), we are exploring classification models for analysis.

Features given in the data set most likely represent characterstics about consumer behavior (history of clickthroughs, site visitiation, etc.), the ads themselves (product, creative approach, placement, etc.) and general metrics such as the date the ad was published. However since there is no visibility into what each feature represents, our challenge is to make our predictions based on the data alone. With over 6 million records to train each day (~45 million per week), this will require a scalable approach.

## Dataset 
The data for this project is available here:
http://labs.criteo.com/2014/09/kaggle-contest-dataset-now-available-academic-use/

Read more about the data at the Kaggle competition website here:
https://www.kaggle.com/c/criteo-display-ad-challenge

## Dataset Introduction 

The training dataset consists of a portion of Criteo's traffic over a period of 7 days. Each row corresponds to a display ad served by Criteo and the first column indicates whether this ad has been clicked or not. The positive (clicked) and negatives (non-clicked) examples have both been subsampled (but at different rates 75% - 0 Class, 25% - Class) in order to reduce the dataset size.

There are 13 numerical features (mostly count features) and 26 categorical features in this dataset. The values of the categorical features have been hashed onto 32 bits for anonymization purposes. The semantic of these features is undisclosed. Some features may have missing values. All the rows are chronologically ordered. The test set is computed in the same way as the training set but it corresponds to events on the day following the training period and does not have the label column. Since, there is no time data available, we are not considering this dataset to be a time series model.

## Key Questions: Features and Model

**1. Which features are most important in predicting clickthroughs?**

Having this information can help Criteo focus on the metrics that are most critical to their product. With 39 features, there is a high risk of overfitting. We should identify a model that provides an optimal tradeoff between bias and variance. Since we didnt get any metadata about the features, we are relying on EDA and regularization techniques to help us determine the important features and reduce dimensionality of the feature space.

**2. Which machine learning approach not only provides the highest accuracy in predicting clickthroughs, but is also scalable enough to be useful in a production environment?**

As internet patterns and product choices change rapidly, the ideal model should be trained daily to update the following day's retargeting model. Scaling would help us achieve shorter training times than processing records sequentially. Any ML algorithm which can be trained using associative and commutative properties (ex. simple addition, with no state dependencies) such as Batch Logisitc Regression or Tree Algorithms based can be used for scaling the training approach.

## Resources
Note that ‘Click Through Rate Prediction’ is not a single algorithm like ‘Naive Bayes’ but rather a goal which can be achieved through a number of different methods. There is a lot of literature out there about binary classification, ensemble methods, factorization machines, collaborative filtering and about the original Kaggle Competition. Do not feel pressured to implement any one approach -- instead try to get a sense for the space and then quickly narrow down an approach you will wrap your head around. Here are some reading materials to get you started.
* https://www.dropbox.com/s/s4x7wp8gjsh021d/TISTRespPredAds-Chappelle-CTR-Prediction-2014Paper.pdf?dl+=0
* https://www.csie.ntu.edu.tw/~r01922136/slides/ffm.pd
* https://www.dropbox.com/s/iozods194twg2pv/MLParis2015-excellent-Sldies.pdf?dl=0
* http://statweb.stanford.edu/~jhf/ftp/trebst.pdf
* https://www.dropbox.com/s/2n8uekjwpaur3bj/Deep-Learning-for-Criteo-Documentation.pdf?dl=0
* https://arxiv.org/pdf/1711.01377.pdf
* https://arxiv.org/pdf/1701.04099.pdf
* https://research.fb.com/publications/practical-lessons-from-predicting-clicks-on-ads-at-facebook/
* https://www.csie.ntu.edu.tw/~r01922136/slides/kaggle-avazu.pdf



##How to run GCP cluster on jupyter: 
https://cloud.google.com/dataproc/docs/tutorials/jupyter-notebook
