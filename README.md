# ML-attacks
In this repositors we will try to demonstrate ML inference attacks.

# Data:
The data is the Nursery schoold social status data which is available on the Internet. It has an sahpe of (12960, 9):


A short snip of data is here.

![image](https://user-images.githubusercontent.com/71256734/187061773-737652e1-1b08-4b6b-83a1-10480896cdb6.png)

#Features, and a quick look inside

* features_names = ["parents", "has_nurs", "form", "children", "housing", "finance", "social", "health", "label"]
* 
* parents:['usual', 'pretentious', 'great_pret']
* data['has_nurs'].unique() #['proper', 'less_proper', 'improper', 'critical', 'very_crit']
* data['form'].unique() # ['complete', 'completed', 'incomplete', 'foster']
* data['children'].unique() # ['1', '2', '3', 'more']
* data['housing'].unique() # ['convenient', 'less_conv', 'critical']
* data['finance'].unique() # ['convenient', 'inconv']
* data['social'].unique() # ['nonprob', 'slightly_prob', 'problematic']  
* data['health'].unique() #['recommended', 'priority', 'not_recom']
* data['label'].unique() #['recommend', 'priority', 'not_recom', 'very_recom', 'spec_prior']

