# Identifying Fraudulent Claims using PCA and K-means Clustering
**Project Update:** The current version of the Jupyter Notebook is being restructured to facilitate the runtime. The EDA, Wrangling and Modeling components will be situated in seperate notebooks. RAndom Forest will be added to our final approach.  
## Background 
Healthcare fraud not only involves falsifying patient encounter information but also collusion with other providers.  In exploring the unique challenges of properly classifying fraudulent claims, this project used  a dataset from a Kaggle project with a similar goal. Classifying fraudulent claims rather than fraudulent providers is more informative in this content given that providers are not always going to be fraudulent for practical reasons. 
## Data Wrangling Methodology
 1. Re-merging Datasets : The original dataset partitioned the original outpatient, inpatient and beneficiary files into separate test and training datasets. Since we will be using unsupervised learning to classify  fraudulent providers/claims, all of the features will have to be numeric. Hence, the test and training set for the inpatient, outpatient and beneficiary datasets were remerged to make the data wrangling process more efficient. 

 2. Handling NaNs with Care: Due to the nature of our inquiry, some types of omission might be a telling trait of a fraudulent activity especially in features that might have a heavier weight in claims like the list or type of diagnosis codes. Therefore, NaNs are for the most part retained and converted to 0  to accommodate our algorithm specifications. However, it would be interseting to see how our results would vary if these values were dropped. 

3. Re-coding Provider Ids : Prefixes like ‘PHY’ and ‘PRV’ in features that reference providers were removed and the remaining numeric values were converted to integers.

4. Deriving Deltas from Dates : Dates were aggregated to new columns with the ‘deltas’ of features that were recorded as dates. For instance, the new feature ‘ClaimDays’  was derived from the recorded claim start and end dates. The derivation of ‘Age’ and ‘AdmitDays’  were derived using the same approach.

 5. Re-coding Claim Diagnosis Code : Non numeric characters in Diagnosis codes were replaced with ‘99’. We do this since E123 is unique from 123 hence a simple omission will be misleading.The value ‘99’ was chosen since the resulting integer value of these diagnosis codes will be outside the natural range of the diagnosis codes without the non-numeric characters and therefore we are able to distinguish these points in the vector space.  

## EDA 

## PCA 
**A. Principal Component Analysis** </p> 
</p> 

**B. Graphical Representation of the Components** </p> 
**N=50**</p>
  </p> 
<img src="https://user-images.githubusercontent.com/29220349/131052992-89dc90c9-1e22-4923-8bc4-32e49a62c2d3.JPG" width="90%"></img> <img src="https://user-images.githubusercontent.com/29220349/131052994-154553ef-e8d1-4560-8f90-36b25359e747.JPG" width="90%"></img> <img src="https://user-images.githubusercontent.com/29220349/131052999-7f8f1320-c5e9-4e56-95b8-11e7b1f66d6e.JPG" width="90%"></img> 
</p>
**N=26**
<img src="https://user-images.githubusercontent.com/29220349/131053245-8a8d3337-3767-49c0-bed9-dd9ebfc7200d.JPG" width="90%"></img> <img src="https://user-images.githubusercontent.com/29220349/131053248-3a3663fa-7f31-4e43-b73f-7e2a5f8a7fdd.JPG" width="90%"></img> 

## K Means </p>
**K=20**</p>
<img src="https://user-images.githubusercontent.com/29220349/131053964-9b0fdbb7-f3f4-447c-8946-cf032505aaa6.JPG" width="90%"></img> <img src="https://user-images.githubusercontent.com/29220349/131053966-fc141299-e6a5-409f-9683-0e0a5ca37810.JPG" width="90%"></img> 
</p>
**K=35**
<img src="https://user-images.githubusercontent.com/29220349/131054171-ac0a5389-1553-49a0-ab83-6b84d574a601.JPG" width="90%"></img> <img src="https://user-images.githubusercontent.com/29220349/131054176-47bdb6e8-1c40-4670-aa66-233fa36c4916.JPG" width="90%"></img> 



## Analysis 
. </p> 
**Insights from PCA and Possible Approaches** </p> 
. </p> 
**Insights from K means** </p> 
. 



