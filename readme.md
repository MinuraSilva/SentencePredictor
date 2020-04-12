Data Source: [Cook County Government Open Data](https://datacatalog.cookcountyil.gov/Courts/Sentencing/tg8v-tm6u)

## Links to Notebooks
1. [Data Cleaning](https://github.com/MinuraSilva/Sentencing/blob/master/Sentencing_data_cleaning.ipynb) - A lot of code but not much interesting here.
2. [Exploratory Data Analysis](http://nbviewer.jupyter.org/github/MinuraSilva/Sentencing/blob/master/Exploratory_data_analysis.ipynb) - This is the link to nbviewer for dynamically displaying the file hosted on this repository. This has a lot of nice plots and analysis.
3. [Predictive Model](https://github.com/MinuraSilva/Sentencing/blob/master/Model_prediction.ipynb) - This is a model to predict the sentence for a given crime.

## A Story of [Race,] Crime and Punishment
This Exploratory Data Analysis attempts to display interesting trends found in the Cook County [Sentencing Dataset](https://datacatalog.cookcountyil.gov/Courts/Sentencing/tg8v-tm6u) including those on race, age, and gender.<br><br>
Before we dive into the data, this is a brief excerpt of Cook County taken from [Wikipedia]((https://en.wikipedia.org/wiki/Cook_County,_Illinois)):
>Cook County is the most populous county in the U.S. state of Illinois and the second-most-populous county in the United States after Los Angeles County, California.<br>
Its county seat is Chicago, the most populous city in Illinois and the third-most-populous city in the United States.

The Cook County Sentencing Dataset is made available through [Cook County Government Open Data Portal](https://datacatalog.cookcountyil.gov/) which describes it as follows:
>The sentencing data presented in this report reflects the judgment imposed by the court on people that have been found guilty.<br>
Each row represents a charge that has been sentenced.

### Notes about this Dataset
This is a large dataset of 236,000 examples containing, among other features, race, age, gender, offense commited and punishment imposed.<br>
Most of the examples dates to between \<insert date range\>.
<br>
<br>
From a data analyst's perspective, this dataset has a few drawbacks:
- First: There is no documentation beyond a short and often unhelpful description of each column.
- Second: There is no information on whether this dataset is complete
- Third: There obvious errors which could be determined from the context of the other columns of an example.
- Fourth: The data is inconsistent between rows, For instance, a Life Sentence can appear in one of two columns.

Despite these issues, this dataset is an important resource given the broad societal and political implications of the events that underlie each data point.<br>
It is made all the more valuable given I couldn't find a similar public dataset published by another government anywhere in the world.<br>
This is surprising given how useful this dataset is - but perhaps it is not in the best interests of governments to hand over such data voluntarily.<br>
This particular dataset, for instance, shows the very significant relationship between race and crime which is already [well documented](https://en.wikipedia.org/wiki/Race_and_crime_in_the_United_States).

### Data Cleaning
I have manually inspected and analyzed the dataset (see Preliminary_Exploratory_data_analysis.ipynb) for errors and either removed the offending rows or tried to coerce it to a reasonable value where possible.<br>
Around 2% of the original rows were found to have errors and discarded. The actual number of rows with errors is almost certainly higher because
societal and political importance.<br>
I have made several assumptions in cleaning the data which can be seen in the Sentencing_data_cleaning.ipynb notebook.

### Warnings on the analysis of this Dataset
A significant issue with this dataset is that no information is provided on whether this dataset is complete, and if not, whether the sampling is unbiased.<br>
This makes any conclusion drawn from this dataset potentially unrepresentative of crime in general in Cook County.<br>
I have looked for obvious biases in the dataset (see Preliminary_exploratory_data_analysis.ipynb) and not found obvious signs that the sampling is skewed.<br>
Going forward, I will assume that the dataset is a representative sample.

### Limitations of my unnderstanding of law and the judicial system
Being a Computer Science major and having a fairly limited understanding of the judicial system, I have had to frequently look online to make sense of the dataset.<br>
Because of this it is certainly possible that I misinterpret the data or my findings, so this is a blanket warning to take my findings with a grain of salt.<br>
