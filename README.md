# Phase 1 Project Description
PROJECT PROPOSAL FOR MICROSOFT FILM STUDIO
# DATA UNDERSTANDING
The data will be sourced from the box office results of films released in a specific time.
This data will include the film titles,genre, budget, gross revenue, releasedates, and other relevant information
# DATA ANALYSIS:
•Data analysis techniques such asvisualization of data using bargraphs , scatter plot and pie charts will be used to identify and
analyze patterns and trends in the data.
# The necessary files and libraries were imported using the codes below
import pandas as pd
import numpy as np
import scipy
import matplotlib.pyplot as plt
import matplotlib.figure
import seaborn as sns
%matplotlib inline

# The files wrere loaded to Dataframes as shown below from TN.MOVIE.BUDGET.CSV FILE and displayed by the code below
# Reading the file
dt=pd.read_csv('tn.movie_budgets.csv')
# determing the 
print(dt.shape)
# Displaying the first five datasets in our file
dt.head()
# Displaying the bottom of the datasets
dt.tail()
# Checking the datatypes in our dataset
dt.info()
## Loading files from BOM.MOVIE_GROSS.CSV FILE to Dataframe  and Reading using jupyter notebook
# Reading the content of the file
bom=pd.read_csv('bom.movie_gross.csv')
# Determining the number of records in the dataset
print(bom.shape)
# previewing the first five data sets in the file
bom.head()
# Previewing the bottom of the dataset
bom.tail()
# checking columns datatypes
bom.info()
# Reading RT.MOVIE_INFO.TSV
# Reading the content of the rt.movie_infor 
rt = pd.read_csv('rt.movie_info.tsv',sep='\t')
# preview of the first 5 datasets in the file
rt.head()
# Previewing the bottom of the dataset
rt.tail()
# checking the datatypes
rt.info()
# Loading data to dataframe from TMDB.MOVIES.CSV and reading using jupyter notebook
tmdb=pd.read_csv('tmdb.movies.csv')
# Showing the records in the file
print(tmdb.shape)
tmdb.head()
# Previewing the bottom of the dataset
tmdb.tail()
# checking the datatypes of the datasets
tmdb.info()
# After reading the files cleaning was necessary so as to obatin the intended results using the cleaned files.The files were cleaned and stored to their respective clean files using jupyter notebook as shown by the following codes
# Cleaning the file so as to obtain cleaned csv file
# dropping rows with NaN values
dt.dropna(axis=0, how='any',subset=None, inplace=True)
# dropping columns with NaN values
dt.dropna(axis=1, how='any',subset=None, inplace=True)
dt.to_csv('dtcleaned_csvfile.csv', index=False)
# Cleaning the file so as to obtain cleaned csv file
# dropping rows with NaN values
bom.dropna(axis=0, how='any',subset=None, inplace=True)
# dropping columns with NaN values
bom.dropna(axis=1, how='any',subset=None, inplace=True)
bom.to_csv('bomcleaned_csvfile.csv', index=False)
pd.read_csv('bomcleaned_csvfile.csv')
# Cleaning the file so as to obtain cleaned csv file
# dropping rows with NaN values
rt.dropna(axis=0, how='any',subset=None, inplace=True)
# dropping columns with NaN values
rt.dropna(axis=1, how='any',subset=None, inplace=True)
rt.to_csv('rtcleaned_csvfile.csv', index=False)
pd.read_csv('rtcleaned_csvfile.csv')
# Cleaning the file so as to obtain cleaned csv file
# dropping rows with NaN values
tmdb.dropna(axis=0, how='any',subset=None, inplace=True)
# dropping columns with NaN values
tmdb.dropna(axis=1, how='any',subset=None, inplace=True)
tmdb.to_csv('tmdbcleaned_csvfile.csv', index=False)
pd.read_csv('tmdbcleaned_csvfile.csv')
# Using the cleaned data, the information were visualized for better understanding using bar graphs , scatter plot and pie charts as show by the codes below
# Bar graph indicating Domestic gross and movie for cleaned TN.MOVIE.BUDGET.CSV file
dt=pd.read_csv('dtcleaned_csvfile.csv')
data = dt.iloc[:5,:]
plt.bar(data['movie'],data['domestic_gross'],width=0.5,label='domestic_gross')
# Set labels and title
plt.xlabel('Movie') 
plt.ylabel('Domestic Gross') 
plt.title('Domestic Gross / Movie')
plt.show()

# Bar graph indicating Worlwide gross and movie for cleaned TN.MOVIE.BUDGET.CSV file
dt=pd.read_csv('dtcleaned_csvfile.csv')
data = dt.iloc[:5,:]
plt.bar(data['movie'],data['worldwide_gross'],width=0.5)
# Set labels and title
plt.xlabel('Movie') 
plt.ylabel('Worldwide Gross') 
plt.title('Worldwide / Movie')
plt.show()

# Bar graph indicating Box Office and Genre for cleaned RT.MOVIE_INFO.TSV file
pd.read_csv('rtcleaned_csvfile.csv')
# selecting the first 10 rows
rt1 = rt.head(5)
# labels and values
x = rt1['genre']
y = rt1['box_office']

# creating a bar graph
plt.bar(x,y,width=0.5, color='green')

# labelling the graph
plt.xlabel('Genre')
plt.ylabel('Box Office')
plt.title('GENRE VS BOX OFFICE')

# displaying the graph
plt.show()

# Pie chart indicating Domestic Gross for BOM.MOVIE_GROSS.CSV FILE
import pandas as pd
import matplotlib.pyplot as plt

# read csv file
bom = pd.read_csv('bomcleaned_csvfile.csv')

# slice the first 10 rows
bomsliced = bom.head(10)

# prepare the data
labels = bomsliced['title']
sizes = bomsliced['domestic_gross']

# plot the pie chart
plt.pie(sizes, labels=labels, autopct='%1.1f%%', shadow=True, startangle=90)
plt.axis('equal')
plt.title('DOMESTIC GROSS')
plt.tight_layout()
plt.show()

# Pie chart indicating Foreign Gross for BOM.MOVIE_GROSS.CSV FILE
import pandas as pd
import matplotlib.pyplot as plt

# read csv file
bom = pd.read_csv('bomcleaned_csvfile.csv')

# slice the first 10 rows
bomsliced = bom.head(10)

# prepare the data
labels = bomsliced['title']
sizes = bomsliced['foreign_gross']

# plot the pie chart
plt.pie(sizes, labels=labels, autopct='%1.1f%%', shadow=True, startangle=90)
plt.axis('equal')
plt.title('FOREIGN GROSS')
plt.tight_layout()
plt.show()

# Scatter Plot for Runtime and Genre extracted from RT.MOVIE_INFO.TSV
#using python code .read data from file called rael.csv using two columns and 10 rows of data , create a  scatter plot 

import pandas as pd
import matplotlib.pyplot as plt

# read data
data = pd.read_csv('rtcleaned_csvfile.csv', header = None, nrows=5)

# create scatter plot
plt.scatter(data[3], data[10])

# add labels
plt.xlabel('Genre')
plt.ylabel('Run Time')

# show plot
plt.show()
