# Cancer-predictions-
Code
A.SOURCE CODE:

#!/usr/bin/env python

# coding: utf-8 #

In[65]:

import pandas as pd import numpy as np import matplotlib.pyplot as plt import seaborn as sns # ln[66] : df=pd.read_csv('heart.csv') #

ln[67]

df ln[68] :

df.shape #

ln[69]

df.columns.

ln[70]

df.describe()

ln[71]

sns.heatmap(df.isnull())

#

ln[72] :

df.columns #

ln[74] =

sns.countplot(df['target']) #

In[63]:

print(i,df[i].skew()) #

for i in df.columns:

ln[64] :

df['target'].skew()

# In[8]:

df.info() #

In[9]:from sklearn.preprocessing import StandardScaler scaler-StandardScaler() scaler.fit transform(df) #

In[45]: df.corr() # In[10]:

from sklearn.ensemble import Random Forest Classifier

rfc-RandomForestClassifier() # In[11]:

from sklearn.model selection import train test split target=df['target'] df=df.drop(['target'], axis=1) df.columns # In[12]: x train,x test,y train,y test-train test split(df,target,test size=0.2 ) print(y test) # In[13]:

rfc.fit(x_train,y_train) #

In[14]:

from sklearn.metrics import accuracy score,confusion matrix, classification report prediction-rfc.predict(x test) # In[34]:

accuracy_score(y_test, prediction) #

In[35]:

#Randomized Search Cv

#no of trees in random forest

n_estimators=[int(x) for x in np.linspace(100,1200,12)]

#no of features to consider at every split

max_features=['auto', 'sqrt'] #maximum no of

levels in a tree max_depth=[int(x) for x in np.linspace(5,30,6)]

#minimum no of samples to split at every node min samples split-[2,5,10,15,100]

#minimum no of samples required at each leaf node

min_samples_leaf=[1,2,5,10] # In[36]: from sklearn.model_selection import Randomized SearchCV # In[37]:

random_grid={'n_estimators'n_estimators, 'max features' max features, 'max depth':max depth 'min_samples_split':min_samples_split, 'min_samples_leaf:min_samples_leaf} # In[39]: rf=Randomized SearchCV(estimator=rfc.param_distributions=random_grid,scoring='neg_mean_s quared_error',n_iter=10,cv=5, verbose=2,random_state=42,n_jobs=1) # In[40]: rf.fit(x train,y train) #

In[41]:predictions=rf.predict(x_test) #

In[75]:

ln[42]

sns.countplot(predictions) # accuracy_score(y_test, predictions) from sklearn.ensemble import GradientBoostingClassifier gbr=GradientBoostingClassifier(n_estimators=3000,learning_rate=0.05 )# ln[49] gbr.fit(x train,y train) predictions1=gbr.predict(x test)

# ln[48]

# ln\{50\}

accuracy score(y_test, predictions1)
