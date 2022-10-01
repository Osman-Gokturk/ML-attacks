# ML-Inference Attack
In this repository we will try to demonstrate a ML inference attack.

#Workbook and installation. 
we need unicode library for:
we need adversalrial-robustness-toolbox to preprocess the date, split it and . The link to the library can be found here: https://github.com/Trusted-AI/adversarial-robustness-toolbox/blob/main/art/utils.py
the workbook is here in the reposityor. 

# Data:
The data is the Nursery schoold social status data which is available on the Internet. It has an sahpe of (12960, 9):8 features and 1 label.


A short snip of data is here.

![image](https://user-images.githubusercontent.com/71256734/187061773-737652e1-1b08-4b6b-83a1-10480896cdb6.png)

# A quick look to the features, and the lable. There are 8 features and one label, most of which are categorical, including the label itself.

* features_names = ["parents", "has_nurs", "form", "children", "housing", "finance", "social", "health", "label"]

* parents:['usual', 'pretentious', 'great_pret']
* data['has_nurs'].unique() #['proper', 'less_proper', 'improper', 'critical', 'very_crit']
* data['form'].unique() # ['complete', 'completed', 'incomplete', 'foster']
* data['children'].unique() # ['1', '2', '3', 'more']
* data['housing'].unique() # ['convenient', 'less_conv', 'critical']
* data['finance'].unique() # ['convenient', 'inconv']
* data['social'].unique() # ['nonprob', 'slightly_prob', 'problematic']  
* data['health'].unique() #['recommended', 'priority', 'not_recom']
* data['label'].unique() #['recommend', 'priority', 'not_recom', 'very_recom', 'spec_prior']

# Data preprossesings:
* remove rows with missing labels
* remove  too sparse label value "recommend" as it has only 2 instances in the data set.
  * data['label'].value_counts()
  * ![image](https://user-images.githubusercontent.com/71256734/187063770-77059604-581b-4f65-b9f4-9f13a5aabae2.png)
* fill missing values in Children data  with 0.
* if  for other categorical X matrix data, fill with "other"

* children contains 0,1,2,3 more. we replace more as  "4"
*  "social" feature is coded as 1 for problematic, and 0 for other two  categories. 
*  for features "parents", "has_nurs", "form", "housing", "finance", "social", "health", [all features except "children] if it is not mentioned fill with "other" category. This way, a new category is added for each feature .

* They have coded label categorical values to numerical classes  as (0,1,2,3) [ recall we omited "recommend", see above]. But for the independent features or X matrix data, they implemented one-hot-coding ( making an extra feature for each category in the feature).

* Eventually we have a matrix of X data for 22 columns: as for each type we should have one one-hot collumn, we would have  3 parents, 5 nurs,3 form,children 1,housing 3,  finance 2, social 1, health 3, =21.  We could have extra 6 columns coming from filling empty with other (actually 7, but we will handle "social" seperately.  Also, It is not for sure that each feature would have some missing values and we will fill them with "other". Because of this reason, we actually have only one featrue in plus.  we have 23  columns instead of 21.  

# Train-test split, Model, Fitting, Scores,
test_set was done for 0.8. . Inıtally there were  12960 rows,  somes were dropped. and the eventual 0.2 Train, 0,8 Test is as following:  

 * XTrain.shape #(2591, 22)
 * XTest.shape #(10365, 22)

## Baseline Accuracy
Baseline accuracy simply condsider a classifier which does nothing. hense, it refers simply to the frequency of of the labels unique values. actually their squares see https://stats.stackexchange.com/questions/67528/how-do-i-calculate-random-baseline.
For our case, in the yTest dataset, the frequencies and baseline accuracy is as following:
![image](https://user-images.githubusercontent.com/71256734/187066545-bc555d92-73cb-4b7e-a3f9-b620dcd0f19e.png)

## Model of DecisionTreeClassifier
one import libraries, define the modelName, fit the model on Xtrain and yTrain. Then apply for Xtest. 
As we have the yTest values, we can invoke for scores. 



