# Active Learning with SVMs for BankNote-Authentication-Dataset

 This is a binary classiﬁcation problem. 
 
 Comparison between Active and Passive Learning on the BankNote Authentication using Support Vector Machines
 
 # Dataset
 
  https://archive.ics.uci.edu/ml/datasets/banknote+authentication

# Procedure 

•	Passive Learning:  

    o	I shuffled the dataset and then separated out 472 datapoints as Test Data. This part of the problem made use of LinearSVC from the classes of SVMs in the sklearn library.

    o	A 10-fold Cross validation technique was achieved via the use of GridsearchCV from the sklearn library.

•	Active Learning:  

    o	To perform active learning instead of picking 10 random datapoints from the X_train_remaining(say train_buffer) at each iteration to train the model, I utilized the decision_function in the LinearSVC class.

    o	The following code provided me with a vector of the remaining training data and their distance from the hyperplane:
      
       	X_margin = clf.decision_function(X_rest) 
       	X_margin = np.abs(X_margin)

    o	I then put this in a dictionary and sorted it preserving their index (as the indices will help me pick the datapoints from the remaining train_buffer).

    o	These 10 are the closest datapoints to the hyperplane, thus they were added to the training set and removed from the buffer for the next iteration.
    
•	Monte Carlo Simulation
  
    o	In order to perform the Monte Carlo simulation of the data, both active and passive learning strategies were experimented on the data.

