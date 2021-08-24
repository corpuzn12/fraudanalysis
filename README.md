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
We modeled our dataset  using 2 versions of the same dataset. The first version contained all 70,000+ entries while the second version is only composed of 30,000 entries. The full dataset and the smaller dataset were both able to achieve a cumulative explained variance ratio around the value  .77 and so the smaller dataframe is a good proxy for the larger dataset.</p> 
**Graphical Representation of the Components** </p> 
The graph of the  full dataset with c= 30 components is similar to the smaller dataset with c= 28. The black graph  represents the full dataset while the orange graph represents the smaller dataset. In both graphs, it is evident that there is a central focal point for the components and an outer perimeter with a more sparse distribution of the components. 

## K Means </p>
We also use a smaller dataset for the k means model. We uses k = 20 and k= 4 as parameters in our models which yielded MSE  scores in the range of 45-49 for the kmeans4 model and a range between 32-49  for the kmeans20 model. These MSE scores are not particularly good but upon looking at the overall distribution of values in each cluster, it is evident that some clusters tend to have either larger values or smaller values in each cluster. This gives some indication that the larger clusters probably belong to the main cluster and the smaller clusters are the groups outside it just as depicted in the PCA graphs.

## Analysis 
Our analysis was greatly hampered by computational issues but some patterns still managed to surface. It would seem that there exists a central cluster or group and around are other types of claims that are different from the majority. </p> 
**Insights from PCA and Possible Approaches** </p> 
PCA  was able to depict the existence of the central cluster and the main cluster persists in the smaller dataset. It is possible that the main cluster is composed of all the legitimate claims and claims that did not make it to the main cluster are different or suspicious in some way.  If this is true, it might be wise to remove the claims that belong in the main cluster and just study the claims that were deemed different enough by our model. From here, we can pick the ideal number of components using the cumulative explained variation score. If we are able to pick a very small value for c, we can go through each component and evaluate the features that consistently were at 0.0 value wise so that we can drop these  features, run a new PCA model  and perhaps pick out the features that are dominant in suspicious claims. Our dataset is comprehensive enough that we can perhaps discern if suspicious  claims tend to be in patients with chronic illnesses or certain types of providers. </p> 
**Insights from K means** </p> 
We are able to pursue a similar approach with the k means model. Once a baseline model with a decent MSE score has been discovered, we can investigate the claims that get clustered away from the primary clusters. We can check if clusters form among the claims that were clustered away from the main cluster so that we can understand other distinctions between the ‘suspicious’  claims. We can go back to PCA to gain some context on what features are dominant in these clusters. 



