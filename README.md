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

# CODING AND OUTPUT:
    import pandas as pd
    df=pd.read_csv("/content/Encoding Data.csv")
    df

    ![318691387-9a445ed3-f79e-46ed-8493-a0138abde135](https://github.com/user-attachments/assets/92642f9b-4f9a-4d0e-b1bc-1e24b14d6f87)

    from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
    pm=['Hot','Warm','Cold']
    e1=OrdinalEncoder(categories=[pm])
    e1.fit_transform(df[["ord_2"]])

  ![318692227-c5ae2314-6f2b-4d93-92b3-f44d1b74015a](https://github.com/user-attachments/assets/1f072c1b-9364-4d06-91dd-8f76f670216d)

    df['bo2']=e1.fit_transform(df[["ord_2"]])
    df
![318692322-4ae17d2a-aa22-4340-9faf-8567549250f6](https://github.com/user-attachments/assets/01ef1378-7d72-4ff5-85fc-8d48521b28e1)
     
      le=LabelEncoder()
      dfc=df.copy()
      dfc['ord_2']=le.fit_transform(dfc['ord_2'])
      dfc
      
 ![318692437-2249ccf3-4a16-462b-b745-677312c7fd42](https://github.com/user-attachments/assets/6da2d0a1-bdcb-4a70-8842-e2d85ffdb5f4)

    from sklearn.preprocessing import OneHotEncoder
    ohe=OneHotEncoder(sparse=False)
    df2=df.copy()
    enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))

![318692763-d2714505-ceae-48c6-b428-fc421aaa735d](https://github.com/user-attachments/assets/b5c14bc1-580b-47a5-914b-92645889030d)
    
    df2=pd.concat([df2,enc],axis=1)
    df2
![318692827-b4b4c5b2-9bc8-4f41-8649-096999696847](https://github.com/user-attachments/assets/98d4025a-4eb7-4139-aa9b-26b354b24628)

    pd.get_dummies(df2,columns=["nom_0"])
    
![318692921-e56e11b0-9489-41a5-973c-e32fca8f9840](https://github.com/user-attachments/assets/e0a587a1-85e4-408b-a022-67f019dc5ab1)

    pip install --upgrade category_encoders
    
![318693032-0711d42f-4456-4222-8334-f183bc7c2385](https://github.com/user-attachments/assets/c27f22be-13de-4f06-84ff-487c7fefa154)

    from category_encoders import BinaryEncoder
    df=pd.read_csv("/content/data.csv")
    df
    
![318693230-3d2f8b4c-0ffc-4754-8c1b-ad637c727c9b](https://github.com/user-attachments/assets/eab9b011-cde6-4e30-a1ce-348058ed423f)

    be=BinaryEncoder()
    nd=be.fit_transform(df['Ord_2'])
    dfb=pd.concat([df,nd],axis=1)
    dfb1=df.copy()
    dfb
    
![318897767-781ddd71-1fc6-499b-9234-b83778405580](https://github.com/user-attachments/assets/b792872b-d8dd-4be5-b60a-2e6f31aaaba1)

    from category_encoders import TargetEncoder
    te=TargetEncoder()
    CC=df.copy()
    new=te.fit_transform(X=CC["City"],y=CC["Target"])
    CC=pd.concat([CC,new],axis=1)
    CC

![318897871-6f1877a4-9ba9-45d6-8df2-38fdc103a0ef](https://github.com/user-attachments/assets/658a8709-e9ad-4442-aab8-de73104279c4)

    import pandas as pd
    from scipy import stats
    import numpy as np
    df=pd.read_csv("/content/Data_to_Transform.csv")
    df
![318897982-63cbb12a-e9eb-447e-855a-e56c706bbfa9](https://github.com/user-attachments/assets/a5d93237-e7cc-42c0-8927-c296ea78f499)

    df.skew()
  ![318898092-3d04bbce-76dc-4571-8c8d-5aad234c1766](https://github.com/user-attachments/assets/000ca5e8-c547-4e55-96b2-a0135252a889)

    np.log(df["Highly Positive Skew"])
![318898189-7247340c-6488-4b75-9deb-0ad3f10e03fd](https://github.com/user-attachments/assets/ae445898-fa69-48d7-82cb-a42a097c7212)

    np.reciprocal(df["Moderate Positive Skew"])
  ![318898261-71ae0399-a828-406a-93a6-0e36cc31e249](https://github.com/user-attachments/assets/d1a6e2e6-5107-4dba-a00b-3a6e8e807e50)

    np.sqrt(df["Highly Positive Skew"])
    
![318898327-9b500fd0-9b55-4397-b1e8-364652aca983](https://github.com/user-attachments/assets/9e0ec8c3-9333-4838-b466-285558179974)

    np.square(df["Highly Positive Skew"])
  ![318898423-d243323b-c97e-4c55-a41f-f76d176e6461](https://github.com/user-attachments/assets/114d5e51-fb6a-4465-9c26-a8f1d6c8d0dd)

    df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
    df
![318898509-758eaaba-b780-4fee-8487-d8242a9d6148](https://github.com/user-attachments/assets/97f09dd3-fde2-44f4-8a7d-928d45c0c917)

      df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
  
  ![318898927-4945b8c6-e27d-4526-9032-0c0aeb9ab576](https://github.com/user-attachments/assets/80afced8-88bf-429a-bdef-5c227dadc020)

    import seaborn as sns
    import statsmodels.api as sm
    import matplotlib.pyplot as plt
    sm.qqplot(df["Moderate Negative Skew"],line='45')
    plt.show()
![318899248-52a7553c-c1bd-4489-a0cb-b13a27684c23](https://github.com/user-attachments/assets/fc2e69ca-bcb5-40c2-b673-9ff7321586da)

    sm.qqplot(np.reciprocal(df["Moderate Negative Skew_1"]),line='45')
    plt.show()
![318899545-3688ed78-4920-4cd4-9e33-4420fc790b8d](https://github.com/user-attachments/assets/40d139c2-17a9-459b-a23e-72afea0330fc)
    
    from sklearn.preprocessing import QuantileTransformer
    qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
    
    df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
    
    sm.qqplot(df["Moderate Negative Skew"],line='45')
    plt.show()
    
![318899696-9ef5152c-d766-48e1-857c-a7dbfde4e648](https://github.com/user-attachments/assets/4a6616b2-4460-4cd5-8d25-7dd48375c59d)
    
    df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
    sm.qqplot(df["Highly Negative Skew"],line='45')
    plt.show()

![318899799-fde4b296-88ec-46ad-b6f3-2cf2b64a15f2](https://github.com/user-attachments/assets/8ad85325-86e6-4908-8cc6-5154a7fb9c25)


    sm.qqplot(df["Highly Negative Skew_1"],line='45')
    plt.show()
![318899874-57bae70b-8ee0-4ab1-86bf-733d2597089d](https://github.com/user-attachments/assets/c18e8879-de7b-488f-aaca-4722ed1779ce)

    sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
    plt.show()
    
![318900112-3987a28b-3816-41b2-9a9d-6a1cedf8382e](https://github.com/user-attachments/assets/c8f1216f-c395-4a73-8228-95c22215022d)


# RESULT:
       Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.

       
