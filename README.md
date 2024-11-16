# BLENDED LEARNING
# Implementation of Support Vector Machine for Classifying Food Choices for Diabetic Patients

## AIM:
To implement a Support Vector Machine (SVM) model to classify food items and optimize hyperparameters for better accuracy.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

# Algorithm

1. **Load Data**  
   Import and prepare the dataset to initiate the analysis workflow.

2. **Explore Data**  
   Examine the data to understand key patterns, distributions, and feature relationships.

3. **Select Features**  
   Choose the most impactful features to improve model accuracy and reduce complexity.

4. **Split Data**  
   Partition the dataset into training and testing sets for validation purposes.

5. **Scale Features**  
   Normalize feature values to maintain consistent scales, ensuring stability during training.

6. **Train Model with Hyperparameter Tuning**  
   Fit the model to the training data while adjusting hyperparameters to enhance performance.

7. **Evaluate Model**  
   Assess the model's accuracy and effectiveness on the testing set using performance metrics.


## Program:
```
/*
Program to implement SVM for food classification for diabetic patients.
Developed by: VINCY JOVITHA V
RegisterNumber:  212223230242
*/
# Import necessary libraries
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix
import seaborn as sns
import matplotlib.pyplot as plt

# Step 1: Load the dataset from the URL
url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-ML241EN-SkillsNetwork/labs/datasets/food_items_binary.csv"
data = pd.read_csv(url)

# Step 2: Data Exploration
# Display the first few rows and column names for verification
print(data.head())
print(data.columns)

# Step 3: Selecting Features and Target
# Define relevant features and target column
features = ['Calories', 'Total Fat', 'Saturated Fat', 'Sugars', 'Dietary Fiber', 'Protein']
target = 'class'  # Assuming 'class' is binary (suitable or not suitable for diabetic patients)

X = data[features]
y = data[target]

# Step 4: Splitting Data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Step 5: Feature Scaling
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

# Step 6: Model Training with SVM
# Define and train the SVM model with predefined parameters
svm_model = SVC(kernel='rbf', C=1, gamma='scale')
svm_model.fit(X_train, y_train)

# Step 7: Model Evaluation
# Predicting on the test set
y_pred = svm_model.predict(X_test)

# Calculate accuracy and print classification metrics
accuracy = accuracy_score(y_test, y_pred)
print("Accuracy:", accuracy)
print("Classification Report:\n", classification_report(y_test, y_pred))

# Confusion Matrix
conf_matrix = confusion_matrix(y_test, y_pred)
sns.heatmap(conf_matrix, annot=True, fmt="d", cmap="Blues", 
            xticklabels=['Not Suitable', 'Suitable'], yticklabels=['Not Suitable', 'Suitable'])
plt.xlabel("Predicted")
plt.ylabel("Actual")
plt.title("Confusion Matrix")
plt.show()
```

## Output:
![image](https://github.com/user-attachments/assets/f058632c-6dd8-4be8-83b0-4f108c4a6381)
![image](https://github.com/user-attachments/assets/7b5a58df-eede-4aa7-b308-8d543fe6a424)
![image](https://github.com/user-attachments/assets/bd7501e0-1ce8-4264-af28-e0164e663458)
![image](https://github.com/user-attachments/assets/362d3b72-47dd-4dfa-b5a9-dd067ce33792)
![image](https://github.com/user-attachments/assets/f5a38ade-0727-4320-988f-0fd7100b92ef)
![image](https://github.com/user-attachments/assets/e94a5d65-3944-4997-a14d-8a97b6eb07ad)


## Result:
Thus, the SVM model was successfully implemented to classify food items for diabetic patients, with hyperparameter tuning optimizing the model's performance.
