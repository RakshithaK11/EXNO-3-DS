## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set. 
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING:
~~~
Developed By: RAKSHITHA K
Register number:212223110039
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[['ord_2']])
df['bo2']=e1.fit_transform(df[['ord_2']])
df
l=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=l.fit_transform(dfc['ord_2'])
dfc
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
dfs=pd.concat([df2,enc],axis=1)
df2
pd.get_dummies(df2,columns=['nom_0'])
pip install --upgrade category_encoders
from category_encoders import BinaryEncoder
import pandas as pd
df=pd.read_csv("/content/data.csv")
df
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb=df.copy()
dfb
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc['City'],y=cc['Target'])
cc=pd.concat([cc,new],axis=1)
cc
import pandas as pd
df=pd.read_csv("/content/Data_to_Transform.csv")
df
df.head()
df.tail()
df.shape
df.info()
df.describe()
df.skew()
import numpy as np
from scipy import stats
np.log(df['Highly Positive Skew'])
np.reciprocal(df['Moderate Negative Skew'])
np.sqrt(df['Highly Positive Skew'])
np.square(df['Highly Positive Skew'])
df['Highly Positive skew_boxcox'],parameters=stats.boxcox(df['Highly Positive Skew'])
df
df.skew()
df['Moderate Negative Skwe_yeojohnson'],parameters=stats.yeojohnson(df['Moderate Negative Skew'])
df
df.skew()
import seaborn as sns
import matplotlib.pyplot as plt
import statsmodels.api as sn
import scipy.stats as stats
sn.qqplot(df['Moderate Negative Skew'],line='45')
plt.show()
sn.qqplot(df['Highly Negative Skew'],line='45')
plt.show()
sn.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
~~~

# OUTPUT:
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/6ceb30ea-61e6-4b39-a19a-5c262a1dc38d)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/9565fbfa-b53a-44c3-b3c2-fc3905df5241)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/ce6bcdae-85f3-4a71-be11-6c838c3f7d24)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/f85604fd-2f0b-42cb-9809-89b0c4aa2f8b)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/ce9c4f01-f6fb-4863-821f-5178bca0cdd9)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/6a612721-aa11-480b-9635-36fcf92f243d)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/594ad3ff-558e-4f7f-a279-93b418df38fc)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/b3f16f33-99c7-4a9a-9a7c-3308584693a5)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/47205027-f705-4f6b-b4ed-923d685fa072)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/161388fb-e6f8-4f8c-a36c-9f39456dcf22)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/f8275320-2ea8-4ae1-80f8-c923b012f38a)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/d5e9e938-75ce-486f-b0a5-8ec9cf8d42e4)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/eb76d5de-9517-4bd9-af3c-4f27198e0844)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/25cd42ef-ec5c-4298-a28e-00af794d4db3)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/4ab2d238-c3ae-498d-9fa7-9f659a31104f)
![image](https://github.com/RakshithaK11/EXNO-3-DS/assets/139336455/1faee6f1-3034-4c45-b473-313f616337df)

# RESULT:
      This code successfully performs feature encoding and transformation on the given data and saves the encoded data to a file

       
