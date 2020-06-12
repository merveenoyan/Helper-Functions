
![Helpers](https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/05df8cc2-4413-4a7c-93c7-dbf7991b18a7/ddz9cyt-5f90be39-8d7e-4770-8c0a-58d15e6c4890.png/v1/fill/w_1280,h_422,q_80,strp/helpers__1__by_markdownimgmn_ddz9cyt-fullview.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3siaGVpZ2h0IjoiPD00MjIiLCJwYXRoIjoiXC9mXC8wNWRmOGNjMi00NDEzLTRhN2MtOTNjNy1kYmY3OTkxYjE4YTdcL2RkejljeXQtNWY5MGJlMzktOGQ3ZS00NzcwLThjMGEtNThkMTVlNmM0ODkwLnBuZyIsIndpZHRoIjoiPD0xMjgwIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmltYWdlLm9wZXJhdGlvbnMiXX0.bIamkZ4ZFyDYBuz774aBI4RFTNIw1E2CYNtn7li4gY8)
## Helper Functions

This repo consists of helper functions for me, maybe they could help you aswell.

**Heat map with annotations**

    correlation = df.corr().abs()
    plt.figure(figsize=(8,8))
    sns.heatmap(correlation, annot=True)
    plt.show()
**Feature Selection with SelectKBest**

    from sklearn.feature_selection import SelectKBest
    kbest = SelectKBest(k=5)
    k_best_features = kbest.fit_transform(features, target)
    list(df.columns[kbest.get_support (indices=True)])
**Concatenate One Hot Encoded Categorical Variables**

    df = pd.concat([df,pd.get_dummies(df["col"],prefix="col")], axis=1)
    df.drop(["col"], axis=1, inplace=True)
**Scaling**

    from sklearn.preprocessing import MinMaxScaler
    scaler = MinMaxScaler()
    scaled_columns = pd.DataFrame(scaler.fit_transform(df[columns_to_scale]),columns=columns_to_scale)
**Get list of numerical variables**

    num_vars = [ var for var in data.columns if data[var].dtypes != ‘O’]
    
**Get list of categorical variables**

    cat_vars = [ var for var in data.columns if data[var].dtypes == ‘O’]
    
> Author: github.com/merveenoyan



