# Identifying Fraudulent Claims using PCA and K-means Clustering
## Background 
Healthcare fraud is a complex type of fraud that not only involves falsifying patient encounter information but also collusion with other providers.  In exploring the unique challenges of properly classifying fraudulent claims, this project used  a dataset from a Kaggle project with a similar goal. Classifying fraudulent claims rather than fraudulent providers is more informative given that providers are not always going to be fraudulent.
## Data Wrangling Methodology
 1. Re-merging Datasets : The original dataset partitioned the original outpatient, inpatient and beneficiary files into separate test and training datasets. Since we will be using unsupervised learning to classify  fraudulent providers/claims, all of the features will have to be numeric. Hence, the test and training set for the inpatient, outpatient and beneficiary datasets were remerged to make the data wrangling process more efficient. 

 2. Handling NaNs with Care: Due to the nature of our inquiry, some types of omission might be a telling trait of a fraudulent activity especially in features that might have a heavier weight in claims like the list or type of diagnosis codes. Therefore, NaNs are for the most part retained and converted to 0  to accommodate our algorithm specifications. 

3. Re-coding Provider Ids : Prefixes like ‘PHY’ and ‘PRV’ in features that reference providers were removed and the remaining numeric values were converted to integers.

4. Deriving Deltas from Dates : Dates were aggregated to new columns with the ‘deltas’ of features that were recorded as dates. For instance, the new feature ‘ClaimDays’  was derived from the recorded claim start and end dates. The derivation of ‘Age’ and ‘AdmitDays’  were derived using the same approach.

 5. Re-coding Claim Diagnosis Code : Non numeric characters in Diagnosis codes were replaced with ‘99’. We do this since E123 is unique from 123 hence a simple omission will be misleading.The value ‘99’ was chosen since the resulting integer value of these diagnosis codes will be outside the natural range of the diagnosis codes without the non-numeric characters and therefore we are able to distinguish these points in the vector space.  

## EDA 

## PCA 
**A. Principal Component Analysis** </p> 
</p> 

**B. Graphical Representation of the Components** </p> 
 </p> 

## K Means </p>

## Analysis 
. </p> 
**Insights from PCA and Possible Approaches** </p> 
. </p> 
**Insights from K means** </p> 
. 



