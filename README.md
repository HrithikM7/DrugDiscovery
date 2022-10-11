# Drug Discovery 

## Quick Intro
Enclosed is a Jupyter Notebook which uses various Machine Learning Models to predict the bioactivity of a molecule towards inhibiting the Acetylcholinesterase enzyme.

## Dataset
* The dataset was extracted from the ChEMBL Database. The ChEMBL Database is a database consisting of information about various bioactive molecules with drug-like properties. 
* The link to access the CheMBL Database has been provided below : 
* https://www.ebi.ac.uk/chembl/ 

## Problem Statement
By using machine learning, we need to figure out which molecules are more suitable to act as a drug to inhibit the Acetylcholinesterase enzyme. Excess amounts of Acetylcholinesterase in the human body is responsible for causing the Alzheimer's disease. Hence, for treating Alzheimer's disease in patients, it becomes highly important to figure out which drug to give to the patient. 

## Approach
Out of all the features present in the dataset, the main ones are : 
* Standard Type : We filtered out the dataset to consider only molecules having a standard type of IC50. IC50 is defined as "Half-maximal inhibitory concentration (IC50) is the most widely used and informative measure of a drug's efficacy. It indicates how much drug is needed to inhibit a biological process by half, thus providing a measure of potency of an antagonist drug in pharmacological research." according to Wikipedia. 

* Standard Value : Standard Value refers to the amount of drug required to reduce the effect of the enzyme. Lower the value of Standard Value, better the drug.

* Canonical_smiles : Canonical_smiles refers to the chemical structure of the compound. 

Initially, data preprocessing was done to the dataset to handle any null values,duplicate rows, etc. Any rows which had null entries for "Standard Value" and "Canonical_smiles" were removed.

Drugs can be classified into three categories : Active, Inactive, Intermediate based on Standard Value
* Standard Value is less than 1000 : Active
* Standard Value is greater than 10000 : Inactive
* Otherwise : Intermediate

Lipinski Descriptors help us to determine the "druglikeness" of a compound(i.e how well will our body react to the drug).It consists of parameters including the molecular weight, solubility of the compound, number of Hydrogen Donors, number of Hydrogen Acceptors, etc. Lipinski Descriptors were calculated for each drug.

IC50 values were converted into the pIC50 scale so that the scale becomes more uniform. 

Following this we performed EDA(i.e Exploratory Data Analysis), and then the "Mann-Whitney U Test".

By using the "PadelPy" library, I cleaned the Canonical_smiles of the various compounds and computed the fingerprints of the molecules. Fingerprint is defined as "A way to describe a molecular structure that can convert a molecular structure into a bit string". 

Using the "LazyPredict" library, various machine learning models including Decision Tree, Random Forest, ExtraTreesRegressor, KNeighborsRegressor, Linear Regression, etc were tried out. 
After determining the best model, hyperparameter tuning was performed using "GridSearchCV".

At last, a pickle file was created to store the model, so that the model can be used in the future.

## Result
Out of all the models that were tried out, the best result obtained was by : Random Forest w/ Model R2 Score : 57.113%
                                                                                           w/ Mean Absolute Error : 0.8427

## Importance
The field of machine learning has seen a tremendous growth over the past few years, and is only going to grow further in the future.

Being healthy allows a person to live their life to the fullest. When a person is suffering from a sickness/disease, it is crutial for doctors to help them in such a way that they get cured in a quick and smooth manner. 
By using this machine learning model, it is possible to find new drugs which are more effective at curing Alzheimer's disease, by acting as inhibitors to the Acetylcholinesterase enzyme.
This model can further be extended to find drugs for any other enzyme/protein.

## Authors

Hrithik Maddirala  
[@hrithik_m245](https://www.linkedin.com/in/hrithik-maddirala/)


<img src="DSC_0037-01-01.jpeg" width="100">
