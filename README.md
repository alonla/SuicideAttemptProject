# SuicideAttemptProject

How to load the neural network model and predict for given patient.

Get the model.json and model.h5 files to your python environment. 

Load the neural network using the code below:

```
from tensorflow.keras.models import model_from_json
import numpy
import os
 
# load json and create model
json_file = open('model.json', 'r')
loaded_model_json = json_file.read()
json_file.close()
loaded_model = model_from_json(loaded_model_json)
# load weights into new model
loaded_model.load_weights("model.h5")
print("Loaded model from disk")

```

Now you can use the model and make predictions using the model you loaded: 

The input data is in the following order: 

```
['Age','Psychiatric_Diagnosis','Un_Married_Parents','Live_Out_Home','Gender']
```

1 - yes, 0 - no. 

For gender - 1 - female, 0 - male. 

Let's consider a 17 year old patient, who has psychiatric diagnosis(1), unmarried parents(1), living at home(0) and has a female gender(1). 

Predicting:

```
print("suicide attempt risk: ", loaded_model.predict([[17,1,1,0,1]])[0][0] * 100, "%")
```

Getting the risk in percentages for attempting suicide:

```
suicide attempt risk:  24.92157518863678 %
```
