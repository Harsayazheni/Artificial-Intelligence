# Ex.No: 10 Learning – Use Supervised Learning  
### DATE:                                                                            
### REGISTER NUMBER : 212222040052
### AIM: 
To write a program to train the classifier for -----------------.
###  Algorithm:

### Program:
```
from google.colab import drive
drive.mount('/content/gdrive')
#import packages
import numpy as np
import pandas as pd
pip install gradio
import gradio as gr
import pandas as pd
cd /content/gdrive/MyDrive/demo/gradio_project-main
data = pd.read_csv('diabetes.csv')
data.head()
print(data.columns)
x = data.drop(['Outcome'], axis=1)
y = data['Outcome']
print(x[:5])
from sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test= train_test_split(x,y)
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
x_train_scaled = scaler.fit_transform(x_train)
x_test_scaled = scaler.fit_transform(x_test)
from sklearn.neural_network import MLPClassifier
model = MLPClassifier(max_iter=1000, alpha=1)
model.fit(x_train, y_train)
print("Model Accuracy on training set:", model.score(x_train, y_train))
print("Model Accuracy on Test Set:", model.score(x_test, y_test))
print(data.columns)
def diabetes(Pregnancies, Glucose, Blood_Pressure, SkinThickness, Insulin, BMI,Diabetes_Pedigree, Age):
    x = np.array([Pregnancies,Glucose,Blood_Pressure,SkinThickness,Insulin,BMI,Diabetes_Pedigree,Age])
    prediction = model.predict(x.reshape(1, -1))
    if(prediction==0):
      return "NO"
    else:
      return "YES"
outputs = gr.Textbox()
app = gr.Interface(fn=diabetes, inputs=['number','number','number','number','number','number','number','number'], outputs=outputs,description="Detection of Diabeties")
app.launch(share=True)
```

### Output:
https://57ad29b8f77718810e.gradio.live/
![Screenshot 2024-10-09 091826](https://github.com/user-attachments/assets/ff58f015-1013-4992-91c3-c51405b9b876)


### Result:
Thus the system was trained successfully and the prediction was carried out.
