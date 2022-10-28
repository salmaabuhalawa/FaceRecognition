# Face Recognition
This is an implemention face recognition using two different approaches: PCA and LDA.

Utilized the ORL dataset that contained forty classes each consisting of ten photos of one person. Each photo captures a different facial expression for that person and the photos are all grayscale with dimensions (92 x 112). Each photo is unravelled into a vector of dimensions (1 x 10304), with each column representing an attribute. The vectors are then stacked on top of each other in data matrix with a total of (400x10304) dimensions. This matrix was separated into two sets; one for testing and the other for training. Each set includes two hundred photos with dimensions (200x10304).

### PCA:
The PCA function takes two parameters, the training set and alpha, where alpha is the required amount of information. 
• First, the mean is computed for each attribute in the training set 
• The mean is then subrtacted from the training set to center the data. 
• The centered data is the used to compute the covariance matrix. 
• The Eigenvalues and Eigenvectors are obtained from the covariance matrix. 
• After computing the EigenValues, the number of dominant Eigenvectors which will be used are determined the value of alpha. 
• The sliced Eigenvectors are then used as a projection matrix. The training data is projected onto this matrix by multiplying data with the matrix, and the same is done with the testing data afterwards  
• A KNN classifier is used to classify the projected testing set. KNN classifier determinse the label for each element by calculating Euclidean distance and choosing the label based on the nearest K points.

Results of PCA show that the accuracy increases as alpha increases up to to a certain value of alpha then the accuracy decreases.

### LDA:
• The data is divided into forty classes. 
• The mean for each class is calculated as well as the overall mean. 
• Each class is centered by subtracting the mean of the class from the corresponding class. 
• Then, using the centered data the within-class scatter matrix and between-class scatter matrix are calculated. 
• Use these to calculate the Eigenvalues and Eigenvectors. 
• Obtain the projection matrix using the 39 most dominant eigen vectors. 
• The training data is projected onto this matrix in the same way as before, then the testing data is projected.
• Then KNN was used to predict the labels of the testing data then we calculated the accuracy of the predicted labels.

Different values of K for the KNN classifier were used for both algorithms to tune the classifier and the observed results show that in all cases, K=1 yeieled the best results.

### Different train-test splits
• Both PCA and LDA were applied to the same data with changing the ratio of amount of training data to testing data.
• Used a 70/30 training to testing data rather than a 50/50 split and compared accuracies obtained.
• Results showed that the 70/30 split always resulted in higher accuracy scores than the 50/50 split.


The purpose of using PCA and LDA was then changed, where it was required to detect whether an image was a face or a non-face. For the non-faces data, the Pepsi and Cocacola Images dataset from Kaggel was used. Then, the number of non-faces data was changed while keeping the number of faces constant at 200, and the performance was measured through the accuracy.

Results showed that the accuracy increased as the number of non-faces increased up to around 280 non-faces, then the accuracy decreased.
