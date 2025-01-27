# Practical Synthetic Data Generation
Khaled El Emam, Lucy Mosquera, Richard Hoptroff
June 2020

## Chapter 01: Introduction

### Defining Synthetic Data

What is Synthetic Data
- data generated from real data that has the same statistical properties as the real data.
- this means if an analyst works w/ synth data they should similar results as working w/ real data
- 2 types of synth data
    - synthesized from real datasets: build a model to capture the distributions and structure of that real data. (structure means the multi-variable relationships and interaction in the data)
    - not synthesized from real datasets: Created by using existing models or by using background knowledge of the analyst.  
    ![alt text](image.png)   
    ![alt text](image-1.png)    

Benefits of Synthetic Data
- Access to data for a secondary purpose is problematic
- Privacy concerns
- Access to datasets can be hard
    - Public datasets  may lack diversity
- Real data may not exist
- Most common is privacy and commercial sensitivity reasons prevent access
- Synth data can significantly accelerate AI/ML initiatives
    - can be used to train initial model before it is used on the real data set 

Learning to trusted the Synthetic Data
- In the 90s, synth data was generated w/ proposals to use multiple imputation methods
    - Imputing realistic data when there was missing data
    - analyst must know how the data will be used
    - if the model is different, synth data will not reflect real data
- Statistical machine learning models are used for data synth
    - advantage is they can capture the distributions and complex relationships among variables
    - W/ deep learning synthesis, models can be accurate

Other approaches to access data for AIML projects 
- De-identification
    - Transform to remove PII
    - Works well w/ clearly defined methodologies
    - Lots of manual intervention and additional controls
    - 
- Secure multi-party computation
    - allows computations to be performed on encrypted data and typically involves multiple independent entities that perform that computation collaboratively w/o sharing or leaking raw data among themselves
    - Ways to do this
        - secret sharing techniques: Data is randomly split among the collaborators
        - homomorphic encryption techniques: data are encrypted and computations are performed on the encrypted values

Synthetic Data Case Studies
- Very difficult to de-identify complex datasets
    - re-identification attacks are a thing

## Chapter 02: Implementing Data Synthesis
2 components to implement Data synthesis
- Process
    - steps and how to integrate synthesis in to a data pipeline
- structure
    would be operationalized through a synthesis center of excellence

### Data Synthesis Projects
Steps
![alt text](image-2.png)
- Start w/ Real data
- Synthesize
- Utility assessment provide assurance to data consumers that the data utility is acceptable & build trust w/ synthesized data
    - 2 stages
        1. general purpose comparisons of parameters calculated from real and synth. i.e. comparisons of distributions and bivariate correlations. (smoke tests) 
        2. Workload aware: analysis of synth data that are similar to the types of analysis that would be performed on real data
- Privacy Assurance assessment: evaluates the extent real people can be matched to records in the synth data and how easy it would be to learn something new if matches are correct

Data Preparation
- Before synthesis, data likely needs to be prepped
    - data Cleansing to remove errors in the data
    - data Standardization to ensure that all fields are using consistent coding schemes
    - data harmonization to ensure the data from multiple sources are mapped to the same data dictionary
    - linking data from multiple sources
        - it is not possible to link synthetic data b/c the synth data do not match real people
    - data shaping
        - i.e. attribute value pairs are difficult to work w/ in standard statistical analysis tools, and maybe reshaped to tabular


### The Data Synthesis Pipeline
simple 1 line pipeline: 
![alt text](image-3.png)

Likely not that simple; 3rd parties involved
![alt text](image-4.png)

even more complex w/ multiple data sources
![alt text](image-5.png)

then, max complexity w/ multiple data sources & 3rd parties doing prep and synth
![alt text](image-6.png)

or just synth
![alt text](image-7.png)

pipeline will depend on
- Number of data sources
- costs and readiness of data analyst
- availability of trusted 3rd parties
- ability to implement automation 


### Synthesis Program Management



### Best Practices for implementing Data Synthesis


## Chapter 03: Getting Started: Distribution Fitting

### How is Data DIstributed

### Fitting Distributions to Real Data

### Generating Synthetic Data from a Distribution

## Chapter 04: Evaludating Synthetic Data Utility

### Synthetic Data Utility Framework

### Comparing Univariate DIstributions

### COmparing Bivariate Stats

### Comparing Multivariate Prediction Models

### Distinguishability
