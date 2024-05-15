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
```
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
```
# OUTPUT:
       ![321273041-de4abe46-97f3-40f5-9bca-3edabfe5d0cc](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/b22edcc7-101f-4517-a5ba-7a82fdd595cb)
![321273140-29224dc6-df44-4f3a-a1a7-15c858de8727](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/e112623b-7a75-493c-9b5e-d670f0563a5b)
![321273243-f25b7603-fb6e-4e04-a161-cd873a55a65e](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/3cc48fb5-80a3-4e67-a7a6-83a91779c2a5)![321273310-93296b88-2e3d-4d70-a816-3a6c42ec9949](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/f0734f6c-3d9b-434d-8052-2ac04d7c14e8)

![321273372-7c780a63-766e-42ab-bd00-d807c3ad26da](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/5b1d7759-15df-4ccc-abe7-857f5184506c)
![321273451-7e8cc484-0b89-40fa-9c92-a32dd05bfaf2](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/a3bf414d-8df5-4412-9a6e-c7431d925b20)
![321273552-28a3fc55-52fe-431b-99ac-53bac58b4b41](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/0292cc04-f753-4ac3-9574-0e5adacffde0)
![321273702-b9c1faeb-eabc-40fd-b343-a8f3f0003219](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/84c0dc78-908e-4179-8d34-c69b528dcc81)
![321273909-6730aa22-7c87-42f3-8d01-31d238f4f885](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/0f07f807-26a5-4860-89b9-44f8de3d0b68)
![321274044-8390f2d9-91d3-4e6e-9562-ea9995cdf0b8](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/93525573-1ba7-42d4-8ce6-c79a100be8c2)
![321274184-0ae95324-377d-4484-989b-bba6795fe78e](https://github.com/VerginJenifer/EXNO-3-DS/assets/136251012/726fea22-9a53-4d78-b3dd-42450976d35f)

# RESULT:

      This code successfully performs feature encoding and transformation on the given data and saves the encoded data to a file
       
