# Ex02-Outlier
# AIM

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# Explanation:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.


# Algorithm:
Step1: Read the given Data.
Step2: Get the information about the data.
Step3: Detect the Outliers using IQR method and Z score.
Step4: Remove the outliers.
Step5: Plot the datas using Box Plot.

# Program

```
Developed by: GURUMOORTHI R
Register number:212222230042
```
```

import pandas as pd
import seaborn as sns

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df

sns.boxplot(data=df)
sns.scatterplot(data=df)

q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr

low=q1-1.5*iqr
low

high=q3+1.5*iqr
high

aq=df[((df>=low)&(df<=high))]
aq.dropna()

df=df[((df>=low)&(df<=high))]
df.dropna()

sns.boxplot(data=df)
sns.scatterplot(data=df)

import pandas as pd
import seaborn as sns

af=pd.read_csv("heights.csv")
af
sns.boxplot(data=af)
sns.scatterplot(data=af)

min=af['height'].quantile(0.25)
max=af['height'].quantile(0.75)

max
min
iqr=max-min
iqr

dq=af[((af['height']>=min)&(af['height']<=max))]
dq

low=min-1.5*iqr
low

high=max+1.5*iqr
high

qm=af[((af['height']>=low)&(af['height']<=high))]
qm

import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df

sns.boxplot(data=df)
sns.scatterplot(data=df)

z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]

out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
op=d_o(val)
op

 ir=pd.read_csv('iris.csv')
 ir
ir.describe()
sns.boxplot(x='sepal_width',data=ir)

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

sns.boxplot(x='sepal_width',data=delid)
```
# OUTPUT
![image](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/1b6d0c0e-2907-49f3-b423-35746ae81f5f)

![265188915-fa93ac20-632d-4cd8-b76a-68394840a306](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/f320eb8c-9f8e-4434-9d22-d411733ba75c)

![265188955-f2eec7ab-9b53-44bc-af09-befb901029e4](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/91f01ddf-6bbc-462f-8afd-478c24360c37)

![265188978-d2461bb8-3783-4fe8-ba77-c287430ce408](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/461a45c6-0544-47ee-b556-de189bd7d7af)

![265188996-e1767d6c-4928-4770-b641-0ced0bf87b33](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/0b798df4-09b9-4340-b600-4b48dbccb742)

![265189016-d25bfaf1-bd9f-4bab-be51-9f708233beb3](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/6c488845-7aaf-494b-b896-ab71857f25aa)

![265189042-54c42a23-1b12-4815-b7ab-a0f252b2d48d](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/0c80f403-23cf-44e2-961e-20e45509b139)

![265189078-a25c988b-353e-479a-98e4-b222f8120a49](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/7e9d79aa-d329-4102-91b0-0c023467dd18)

![265189108-b9348ba4-c099-4aca-98f8-87535647e524](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/0b0e5ea5-5a99-4b07-a84d-d7b6022ccaa1)

![265189128-62458e3c-31a6-45ff-b98c-fd3505ea37ac](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/8c0deb8e-d0e1-4c75-932f-a2b0c453c2fb)

![265189146-a3f9baf3-040d-4245-ba93-f2155afbcdeb](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/1a3dc17a-f6ca-4c43-b87f-d8094a2441c1)

![265189183-82e11d56-b4c4-4ef5-9725-2ec3c863c757](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/d598c9f1-2e28-4bed-bcde-b8b6eab4d225)

![265189320-6839c0f1-29ed-4026-b8c1-50acd9fdcd4f](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/01a57b6f-07a0-43bd-b5bb-27d4b0cb6a1b)


![265189403-e41a9dee-3de2-472c-8b63-c64c419beaa2](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/f36094d3-430f-4fe6-879e-a4474751c150)

![265189449-5a8c15a3-a066-41bc-8258-0df36b8f3c5f](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/8fcd077d-eeb2-4594-b609-83190259bd88)

![265189468-12ac2ed2-8cb0-408b-8c68-9af01f2e8146](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/54ea381e-1509-4022-90bc-7c40253a6d3a)

![265189742-e4785692-85e1-49c3-a44c-77664609ed8b](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/d567d860-1997-4f9f-9e73-6f5570a96ce0)

![265189908-4ae0bc50-f20e-4bb9-9925-7f0c40901beb](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/5c8281cc-02c6-4b18-be0e-cbf653e3706c)

![265189927-c0ad3428-8644-46b5-98a6-e0d56783c486](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/43ed7311-108f-483a-83d2-875b944e15d6)

![265189951-0b9f2034-cab0-4674-a63f-e8f7ef3c215b](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/566d7268-9dfb-4ca0-9044-420bd2b16606)



![265189973-b5d433c7-f75c-41b4-9297-299ac54ade10](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/e5f274ca-64fe-44ed-bb64-2c233b3050a7)


![265189990-8909a651-a861-469a-89a7-c77d5dda1709](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/f3eb4daa-4892-4fb9-b7df-883c2e544491)


![265190010-ef7b319a-2002-4286-8619-80ac58775efc](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/4cc733a5-5035-476d-b8c6-a961c8bbea2f)

![265190033-2ffd4010-e7d6-4c04-bfd2-f036b2d532ef](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/f9ab4c97-cf9a-4114-ac2b-ba50861b5550)


![265190062-b4b45961-92de-4d0a-a86a-325d9b3e888d](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/10fe65ff-0b84-4fe4-8141-ad1410f59af5)


![265190078-706585bd-abb0-4df9-b53c-4669d3cfb20f](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/0b520541-6906-4042-a722-289452465b86)


![265190103-f08030b4-0e11-4a9c-b500-2ae6ec883669](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/e5b7ccfd-0dff-4762-bcd7-e07eaff612f8)




![265190116-ff40cc12-e462-4cb7-91ed-a26ee384b0c5](https://github.com/gururamu08/ODD2023---Datascience---Ex-02/assets/118707009/eab8bd8c-82a9-4ded-9cf4-2849f53008ca)


# Result
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.




































































































