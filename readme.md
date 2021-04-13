# A Story of [Race, Gender, Other factors,] Crime and Punishment

Data Source: [Cook County Government Open Data](https://datacatalog.cookcountyil.gov/Courts/Sentencing/tg8v-tm6u)

**Summary**
In this project, I attempt to predict a criminal sentence based on information about the crime using a machine learning model (boosted decision trees). The information I use to train the model is from the [Cook County Sentencing Dataset](https://datacatalog.cookcountyil.gov/Courts/Sentencing/tg8v-tm6u) and includes fields with various information on the kind of crime committed, demographic information of the criminal and the criminal sentence. The machine learning model attempts to use all other fields to predict the criminal sentence (I have had to simplify this to simply predicting the categorical kind of sentence, such as probation, boot camp or prison. The model has 69% accuracy (up from 58% baseline accuracy using a dummy classifier). In my opinion, a some of the significant reason for the relatively modest improvement in accuracy are:
1. There is insufficient information contained within the dataset on the crime committed; for instance it may be difficult to tell where an offense for drug posession transitions from being a misdemeanour to a felony.
2. Certain important aspects such as whether the person has previously committed a similar offense are not present in this dataset. This is known to significantly affect the sentence.
3. Many cases involve crimes where the person is charged with multiple offenses. In this dataset, these offenses are presented in separate rows with an identifier to link them together. In these cases, it appears to me that the 'sentence' is the verdict for all of the offenses considered. I have not merged these multiple offenses together (due to time and complexity constraints) and this  will cause issues, such as when a small offense in a multiple offense case has the severe sentence of all the offenses combined.

Information for Users:
- First have a look at the Exploratory Data Analysis Notebook (from the dynamic link below).
- Then go to the Predictive Model notebook where I attempt to predict the type of criminal sentence given information about the crime.
- You probably wouldn't find much interesting in the Data Cleaning Notebook unless you're interested in the decisions I made to clean the data.
    

## Links to Notebooks
1. [Data Cleaning](https://minurasilva.github.io/SentencePredictor/Sentencing_data_cleaning.html) - A lot of code but not much interesting here.
2. [Exploratory Data Analysis](https://minurasilva.github.io/SentencePredictor/Exploratory_data_analysis.html) - This is the link to dynamically displaying jupyter notebook displayed through GitHub Pages. This has a lot of nice plots and analysis.
3. [Predictive Model](https://minurasilva.github.io/SentencePredictor/Model_prediction.html) - This is a model to predict the sentence for a given crime.

The data for this project comes from the [Cook County Sentencing Dataset](https://datacatalog.cookcountyil.gov/Courts/Sentencing/tg8v-tm6u).<br><br>
Before we dive into the data, this is a brief excerpt of Cook County taken from [Wikipedia]((https://en.wikipedia.org/wiki/Cook_County,_Illinois)):
>Cook County is the most populous county in the U.S. state of Illinois and the second-most-populous county in the United States after Los Angeles County, California.<br>
Its county seat is Chicago, the most populous city in Illinois and the third-most-populous city in the United States.


## Notes about the Dataset
The Cook County Sentencing Dataset is made available through [Cook County Government Open Data Portal](https://datacatalog.cookcountyil.gov/) which describes it as follows:
>The sentencing data presented in this report reflects the judgment imposed by the court on people who have been found guilty.<br>
Each row represents a charge that has been sentenced.

This is a large dataset of 236,000 examples containing, among other features, race, age, gender, offense commited and punishment imposed.<br>
Most of the examples date to the previous decade.
<br>
<br>
From a data analyst's perspective, this dataset has a few drawbacks:
1. There is no documentation beyond a short and often unhelpful description of each column.
1. There is no information on whether this dataset is complete.
1. There obvious errors which could be determined from the context of the other columns of an example.
1. The data is inconsistent between rows, For instance, a Life Sentence can appear in one of two columns.

Despite these problems, this dataset is incredibly valuable since, even with a lot of searching, I couldn't find another similar dataset published by another government anywhere in the world.<br>
This might be due of privacy issues or perhaps governments don't want to hand over data which might be used to criticize them.

## Notes on Data Cleaning
- I have manually inspected and analyzed the dataset (see this rather messy [notebook](https://github.com/MinuraSilva/Sentencing/blob/master/Preliminary_Exploratory_data_analysis.ipynb)) for errors and either removed the offending rows or tried to coerce it to a reasonable value where possible.
- Around 2% of the original rows were found to have errors and discarded. The actual number of rows with errors is almost certainly higher.
- The assumptions I have made in cleaning the data along with some commentary can be seen in the Data Cleaning notebook.

### Warnings on the analysis of this Dataset
- A significant issue with this dataset is that no information is provided on whether this dataset is complete, and if not, whether the sampling is unbiased.
- This makes any conclusion drawn from this dataset potentially unrepresentative of crime in general in Cook County.<br>
- I have looked for obvious biases in the dataset (see Preliminary_exploratory_data_analysis.ipynb) and not found obvious signs that the sampling is skewed.
- Going forward, I will assume that the dataset is a representative sample.

### Limitations of my Expertise
- Justicial System: I have an extremely limited understanding of the judicial system (I have had to frequently look online to make sense of the dataset).<br> It is possible that I could have misunderstood certain things about the judicial system which might make the decisions I made during data cleaning and analysis invalid.
- Statistics: My knowledge of statistics extends only to a couple of undergrad statistics courses, so my statistical inferences may be incorrect.
- Machine Learning: For the predictive model, I use machine learning of which the known limitations and ethical issues are [plenty](https://en.wikipedia.org/wiki/Machine_learning#Limitations).
