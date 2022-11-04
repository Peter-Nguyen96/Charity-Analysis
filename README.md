# Charity-Analysis-Challenge-19

*** NOTE: Deliverable 3 is contained within the AlphabetSoupCharity.ipynb file. All checkpoints stored with prefix new_

Purpose: The purpose of this assignment was to create a neural network machine learning model in order to create a binary classifer that will be used to predict if new applicants will be successful if funded by Alphabet Soup. The machine learning model utilized data pertaining to application type, affiliation, classfication, use case, organization type, active status, income, ask amount and special considerations and was labelled with tags to identify successful or unsuccessful campaigns.

Results:
* Data PreProcessing:
  - Since the purpose of this analysis is to predict successful campaigns, the 'IS_SUCCESSFUL' column from the dataset was chosen as the target for the model.
  - Initially, the following columns were chosen as features for the model: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL CONSIDERATIONS, and ASK_AMT
  - the EIN and NAME columns were removed from the input data because they are variables that act more like identifying indexes rather than data that could be considered features or a target
  
 The cleaned input DataFrame:
 
 ![1](https://user-images.githubusercontent.com/108313294/200051737-d2dfb717-797d-4c05-8430-d79e48769fef.png)

* Compiling, Training, and Evaluating Model
  - Initially, there were were 4 total layers, an input layer, two hidden layers and an output layer.  80 layers was chosesn for the first hidden layer since it is roughly twice the number of input layers as the number of inputs to fit the general rule of thumb for starting of 2-3x.  The second layer was reduced to 30 neurons which is closer to the actual number of inputs.  This allowed for reduced training time.  the "relu" activation function was used for both hidden layers to determine the how much each feature added to the probability of a successful funding campaign from 0-1. Since the final result is a binary classifier, the sigmoid function was used for the output layer with only 1 unit.
  - The models were not able to achieve the desired 75% accuracy performance target in testing.
  - Aside from standard scaling, kerastuner was used to optimize neuron/hidden layer counts, and test 'leaky_relu" as an alternative activation function which would apply a small negative value to features that may reduce probability of successful campaigns. A total of 5 hidden layers was used in an optimization attempt. 'STATUS' was removed as a feature in an attempt to clean up data since it may be redundant to IS_SUCCESSFUL in many cases, and "ASK_AMT" had extremly high variability and although it could have been a good feature, it could also add a lot of noise to the data. The feature was therefore removed in hopes that the other features could potentially be adequate to create a model.

![2](https://user-images.githubusercontent.com/108313294/200053777-3558449c-c086-49a4-b3a4-7ee0a4c8944f.png)

Summary:

OVerall, the deep learning model was very close at achieving the desired 75% accuracy rate, however had a significant amount of losses (over 50%) in both the original model, and through attempts at optimization.  Theoretically, if more data reduction was done for example by binning, Logistic regression could be performed.  Since all the data is also in tabular form, random forest models could also be used as an alternative to neural networks.  This could reduce the training time, and force better data cleaning for the analysis.  Logistic regression may sacrifice more accuracy which is undesirable in this case, but random tree does have the potential to be as accurate as the deep learning model utilized.
