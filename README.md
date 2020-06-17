![Helpers](https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/05df8cc2-4413-4a7c-93c7-dbf7991b18a7/ddz9ebz-a8b8ba76-12be-44a6-b2e2-2e71a3da836c.png/v1/fill/w_1280,h_420,q_80,strp/helpers_new_by_markdownimgmn_ddz9ebz-fullview.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3siaGVpZ2h0IjoiPD00MjAiLCJwYXRoIjoiXC9mXC8wNWRmOGNjMi00NDEzLTRhN2MtOTNjNy1kYmY3OTkxYjE4YTdcL2RkejllYnotYThiOGJhNzYtMTJiZS00NGE2LWIyZTItMmU3MWEzZGE4MzZjLnBuZyIsIndpZHRoIjoiPD0xMjgwIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmltYWdlLm9wZXJhdGlvbnMiXX0.NuORQgZXDNMoX9_76S4aM3G9bl_HtdikntfLa9p3Pqk)
## Helper Functions

This repo consists of helper functions for me, maybe they could help you aswell.

## Exploratory Data Analysis

**Heat map with annotations**
```python
correlation = df.corr().abs()
plt.figure(figsize=(8,8))

sns.heatmap(correlation, annot=True)
plt.show()
```

## Feature Selection
**Feature Selection with SelectKBest**
```python
from sklearn.feature_selection import SelectKBest

kbest = SelectKBest(k=5)
k_best_features = kbest.fit_transform(features, target)
list(df.columns[kbest.get_support(indices=True)])
```

## Preprocessing
**Concatenate One Hot Encoded Categorical Variables**
```python
df = pd.concat([df, pd.get_dummies(df["col"], prefix="col")], axis=1)
df.drop(["col"], axis=1, inplace=True)
```

**Scaling**
```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
scaled_columns = pd.DataFrame(scaler.fit_transform(df[columns_to_scale]), columns=columns_to_scale)
```

**Get list of numerical variables**
```python
num_vars = [ var for var in data.columns if data[var].dtypes != ‘O’]
```

**Get list of categorical variables**
```python
cat_vars = [var for var in data.columns if data[var].dtypes == ‘O’]
```

## Deployment
**Using joblib to save models and pipelines**
```python
import joblib

joblib.dump(pipeline, 'model.joblib')
joblib_model = joblib.load('model.joblib')
```

**Using pickle to save models and pipelines**
```python
import pickle
with open('model.pkl', 'wb') as model_file: pickle.dump(pipeline, model_file)
```

> Author: github.com/merveenoyan



