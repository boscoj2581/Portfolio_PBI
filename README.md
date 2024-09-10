# Portfolio_PBI

Relation between Brain Weight and head Size.

Source:  dataset that shows a few variations of head sizes (cm3) and masses of brains (grams) 
Gladstone, R. J. (1905). A STUDY OF THE RELATIONS OF THE BRAIN TO THE SIZE OF THE HEAD. Biometrika, 4(1–2), 105–123. 

In order to apply a linear regression model, we need to establish the relation between the independent variable and the predictive. 


So in this project we determined the correlation coefficient pearson using DAX in Power BI.

What's a correlation coefficient?

![Description](https://github.com/user-attachments/assets/10963664-d5d1-419b-80fa-173af1d9cf5b)

Formula used to calculate Correlation Coefficient pearson:
![CC Pearson](https://github.com/user-attachments/assets/59fc1383-6a56-4170-8f52-809e39ca7b4a)

DAX measure:
      
      Correl_x_y = 
      VAR _muX = CALCULATE([Ave_HeadSize])
      VAR _muY = CALCULATE([Ave_Weight])
            VAR _Num =
                  SUMX(Study_dataset, (Study_dataset[Head_Size]-_muX)*(Study_dataset[Brain_Weight]-_muY))
      VAR _Den1 = 
                 SUMX(Study_dataset,POWER((Study_dataset[Head_Size]-_muX),2))
      VAR _Den2 = 
                  SUMX(Study_dataset,POWER((Study_dataset[Brain_Weight]-_muY),2))
      VAR _Den = SQRT(_Den1*_Den2)
      
      VAR _Corr = DIVIDE(_Num, _Den)
      RETURN _Corr




Look the report Power BI in this link:

https://app.powerbi.com/view?r=eyJrIjoiYzg4Y2M0YTYtZDMyMC00NGY4LTgxYzgtMTgzMmQxNDY5YTQyIiwidCI6ImMzODZkOTcxLTJhNGYtNGRjZi04ZWE0LWJlZGNlYWVlMTljNiIsImMiOjR9
