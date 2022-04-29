# Heart disease prediction Logistic regression
### Executive Summary of the Final Project
Heart disease is the leading cause of death for people of most racial and ethnic groups in the United States. In every 36 seconds in the United States, one person dies from cardiovascular disease. About 659,000 people in the United States die from heart disease each year based on CDC data. There are some key factors, such as high blood pressure, high cholesterol, and smoking, for heart diseases. Some other medical conditions and lifestyle choices, including overweight and obesity, excessive alcohol use, unhealthy diet, physical inactivity, and diabetes, can also place people at a higher risk for heart disease. Additionally, aging can be a reason for changes in the heart and blood vessels that may increase developing cardiovascular disease of a person.

In our study, we analyzed critical factors affecting heart disease and developed a model to predict if the user is prone to heart disease. A detailed dashboard is created which helps to classify patients' current health conditions that are prone to heart related diseases. Using these observations from this application, the user can be informed about whether they are prone to heart disease or not.

### Target Users or Analysis Consumers
Our target users are common people who can use this tool to know whether they are prone to heart disease based on multiple health and lifestyle parameters. The age of the users ranges from 18 to 80+. Here, we analyzed and developed the model based on consumers with different BMIs, alcohol and smoking habits, and history of diabetics, kidney diseases and skin cancer etc.,

### Data Sources
The data for this application was obtained from the Kaggle.com website. The primary information came from Personal Key Indicators of Heart Disease | Kaggle, which was obtained based on the CDC survey data of ~320k adults. This data is collected via survey over a phone call in the year 2020 for United states. The dataset has following columns which were used as attributes in the model.
1.	HeartDisease
2.	BMI
3.	Smoking
4.	AlcoholDrinking
5.	Stroke
6.	PhysicalHealth
7.	DiffWalking
8.	Sex
9.	AgeCategory
10.	Race
11.	Diabetic
12.	PhysicalActivity
13.	SleepTime
14.	Asthma
15.	KidneyDisease
16.	SkinCancer


### Technical Summary

We have primarily used Excel for data transformation and developed complex mathematical models to predict the user is prone to heart disease or not using Excel, Solver, XRealstat add-in and VBA. Tableau/Power BI has been used as the data visualization tool to create interactive dashboards showcasing the useful insights for critical factors affecting heart disease. We have used the GRG Non-linear and newton’s method to find the optimal co-efficients of Logistic regression model. This technique is used for estimating the probability of heart diseases given different health conditions, ages, races, etc. of users. The details of the model development are described below.

  
  ![image](https://user-images.githubusercontent.com/95113910/166076813-c4af5b92-1b82-4942-87a0-92f5c08fe02d.png)

The raw data from the CDC on heart disease is transformed to fit the mathematical model. The data transformation technique used here is one hot encoding. We performed Exploratory data analysis to check the anomalies and the extreme values in the dataset. 
              The dataset is split into train and test on the ratio of 80:20 to train and evaluate the model. We took traditional model building approach by formulating the multiple regression to calculate the regression score. This score helped in finding the probability using logistic regression equation. We found the likelihood followed by log likelihood. To maximize the aggregated value of the log likelihood we used the GRG non-linear Solver method to find the optimal values of co-efficients for the regression model. As this Solver method is prone to stop the execution at local maximum, we verified the optimal solution by comparing it with the newton’s method.
	We developed an excel application to predict whether the user is prone to heart disease or not. This application allows the user to enter the health and lifestyle parameters using the user-friendly form. These values are passed to the VBA code at backend to do the predictions
	
## Outputs
### Step-1: Exploratory Data Analysis
### Raw Data  Data Transformation
The input data had many nominal data. So, to fit a mathematical model we had to convert these nominal data to numerical values. Below are the transformations.
1.	Smoking habit
Yes =1 No = 0
2.	Alcohol habit
Yes =1, No = 0
3.	Stroke history
Yes =1, No = 0
4.	Difficulty in walking
Yes =1, No = 0
5.	Gender
Male =1, Female = 0
6.	Age
18-24 = 1, 25-29 = 2, 30-34 = 3, 35-39 = 4, 40-44 = 5, 45-49 = 6,
            50-54 = 7, 55-59 = 8, 60-64 = 9, 65-69 = 10, 70-74 = 11, 75-79 = 12, 
            80 or older = 13
7.	Race:
White = 1, Black = 2, American Indian/Alaskan Native = 3, 
            Hispanic = 4, Asian = 5, Other = 6
8.	Diabetic condition
Yes =1, No = 2,  
No, borderline diabetes = 3, Yes (during pregnancy) = 4
9.	Physical activity
Yes =1, No = 0
10.	Asthma history
Yes =1, No = 0
11.	Kidney disease history
Yes =1, No = 0
12.	Skin cancer history
Yes =1, No = 0

      To divide the data in Train and test datasets for training the model and validating we used excel Random function RAND. This assigns a random number for each record, and we applied a rule to split the dataset into 80:20 ratio. We observed that even the dependent variable was split in the same ratio without any biasing.

      We used the JMP Software and Correlation Matrix to find the significance of each variable with respect to the dependent variable. We found out that the Sleep time and the Race had p-value much greater than 0.05 depicting insignificance for this predictive modelling.

![image](https://user-images.githubusercontent.com/95113910/166076972-1b57386e-2cf1-4a21-91e7-94ecf3b09923.png)

### Data visualization for the insights

![image](https://user-images.githubusercontent.com/95113910/166077017-a43c92ad-95cc-4a13-9f9f-4d530c7a5e88.png)

The above histogram depicts the effect of BMI and physical activity for each gender on heart disease. This graph is left skewed. The BMI ranging from 25 to 30 for both male and female with physical activity are more likely has suffered heart disease. 

![image](https://user-images.githubusercontent.com/95113910/166077039-51251395-2525-4d09-b7a1-be16488b6651.png)

This above histogram depicts the number of adults suffered from heart disease based on the age. The graph is right skewed and indicates that older people whose age is above 60yrs has suffered more from heart disease.

![image](https://user-images.githubusercontent.com/95113910/166077061-e6d401c0-e1f8-4bbc-bf5a-d2c70dd40d2b.png)

The above pie-chart depicts the count of heart disease based on the race. The major population of US consists of White and Black race which makes up to 88% of the total heart disease patients.


![image](https://user-images.githubusercontent.com/95113910/166077105-f027d62a-dc2e-469b-881a-1ff61c22217f.png)

The above pie-chart depicts the effect of Diabetes on heart disease. A considerable amount of people who were not diabetic had heart disease. This infers that the diabetic factor alone cannot be the deciding factor for a person to have heart disease.


### Step-2: Predictions based on past data of the year 2020 using Logistic Regression model
## Lifestyle and health conditions as Inputs  Predict the possibility of heart disease
Once the data preparation is completed, with the help of excel regression model to fit the data to obtain the co-efficient of independent variables. Regression score is calculated by using these co-efficients and the data points. 
       
### Score = Intercept + Sumproduct (Co-efficients * Data points)
          
Coefficients of multiple linear regression has been used as input for the building Logistic Regression model to obtain the Probability. The probability of heart disease is then calculated using the following function: 

### Probability = Exp (Score)/ (1+Exp (Score))


       Using the Probability values, we found out the Likelihood which explains How likely is the user prone or not prone to heart disease. 

			        If (Dependent variable is TRUE) Then
 				Likelihood = Probability
			        Else
			            Likelihood = (1 – Probability)
			        End-if

       Then we proceed to find the Natural Log of Likelihood. This had to be done to scale down the Likelihood values so that the Solver can handle the data better.
 
                                            Log Likelihood = Ln (Likelihood)


### Model Optimization using GRG Non-Linear Algorithm: -  

To optimize this model, we did summation of the Log Likelihood to set the objective as maximum by changing the regression co-efficient cells. We used Generalized Reduced Gradient non-linear solver method to get the maximum Likelihood value with corresponding regression co-efficients.

This model took almost 50-60 iterations before finding the maximum value for aggregated Log Likelihood. As we know the GRG nonlinear model chooses the step size and direction of propagation to reach the nearest maximum/minimum value, this could result in compromised optimization if the iteration is stopped at local maximum/minimum. To verify if the solution obtained from this model is best optimal solution, we performed the analysis based on Newtons-Raphson method.

![image](https://user-images.githubusercontent.com/95113910/166077236-195cb240-12f8-4f17-9ccd-41ba37ffe2c5.png)

![image](https://user-images.githubusercontent.com/95113910/166077247-aa53d5a1-71e5-417b-92af-be773ece317a.png)

![image](https://user-images.githubusercontent.com/95113910/166077263-e74e0507-e14e-44c9-b670-a4a6cad618a7.png)


### Model Evaluation for trained data:

        We predicted the outcome with the help Probability obtained from the Logistic Regression by using the condition as mentioned below.

	       			If Probability > 0.5 Then
				    Prone to Heart Disease
				Else
				    Not Prone to Heart disease
				End-If

         We built the confusion with the help of Predicted and Actual values and found the precision for True positive and True negative. Accuracy of the model is also calculated using the below formula.
				Accuracy = (TP + TN)/(TP+TN+FP+FN)

![image](https://user-images.githubusercontent.com/95113910/166077280-4f1de8cf-5600-4a24-ab25-78ffe9e589f2.png)

Model Fitting using the Test Data:

        Using the co-efficients obtained from the trained model, we calculated the Regression Score along with the Probability suing the Logistic regression equation. Then we predicted the outcome using the below condition.

				If Probability > 0.5 Then
				    Prone to Heart Disease
				Else
				    Not Prone to Heart disease
				End-If

        We built the confusion with the help of Predicted and Actual values and found the precision for True positive and True negative. Accuracy of the model is also calculated. 

        We observed that the accuracy and precision for test data is approximately equal to that of train data. 
        
        ![image](https://user-images.githubusercontent.com/95113910/166077333-b05087b1-d73f-4d1b-a1d7-80e16953b819.png)


### Model Optimization and Validation Using Newton’s Algorithm: -

The newton’s method is an iterative algorithm for finding a point where function is zero. The outcome of this algorithm is more likely the global optimal solution. The Gradient descent is the first order derivate method algorithm, but whereas in newton’s method applied to optimization is second order derivate method. 

Further to find the optimal solution from this model we set the derivative equal to zero to find the maximum or minimum. Also means this iterative process we perform second order approximation as shown below. 

So, if we start at point X0  , we make the quadratic approximation to find the X(t+1). So now our new minimum is at X1 .   To verify if we are going in intended direction, which is to find minimum or maximum, we observe the shape of the quadratic function. If quadratic approximation function is convex to the main function F(x), then our propagation is in the direction to find the minimum, if our quadratic approximation function concave to main function F(x) our propagation is towards maximum.


![image](https://user-images.githubusercontent.com/95113910/166077357-840518f4-849a-416a-9ab9-dc2f40117f19.png)

![image](https://user-images.githubusercontent.com/95113910/166077366-34e2a78a-a4db-4f61-bb1e-d6e919059d0c.png)

The above diagram shows the path taken by Gradient descent (in Green) and Newton’s method (in Red). As the Newton’s method uses curvature information for propagation i.e the second derivative, it takes a more direct route compared to gradient decent. 

### Observation of Newton’s method optimization for CDC data set: - 

•	The newton’s optimization model only took 15-20 iterating to find the maximum likelihood compared to gradient descent which took approximately 50-60 iteration.

•	The coefficients and maximum likelihood obtained from GRG model and Newton’s method are equal, which verifies the solution obtained from GRG nonlinear is Global maximum value. 


### Step-3: User form for the Prediction Model using VBA

The user will be presented with the user form to check if he/she is prone to heart disease based on the health parameters. A click on the submit button on the user form will pass the control to validation subroutine. This subroutine will check for the Nulls and negative values for three text boxes and null value for one combo box. Physical health parameter should have a value between 0 and 30 whereas all option buttons should be selected.
After successful validation, the control is passed to main subroutine (predict_heart_disease). In this subroutine the below tasks are performed:
•	The categorical value from the option button will be converted into the binary value.

•	The Height and weight values from the user form is passed to the BMI () function to calculate BMI of the user.

•	The value selected for the Age field by the user from the combo box is passed to the Age () function to convert the Age bins to appropriate numerical values.

•	Implementation of the multiple regression with the intercepts, co-efficients and its respective data points of the predictive model to calculate the regression score.

•	Using this Score and Logistic regression expression Probability value is calculated.

•	The obtained probability value is used to determine if the user is prone to heart disease or not.

       Along with the Submit button there is also a Clear option which resets the values entered by the user. 


![image](https://user-images.githubusercontent.com/95113910/166077397-27001d01-cc62-46e6-9456-31a406e9e4a5.png)


### Benefits to Target Audience

The dashboard will help the local health body to spread awareness about key indicators of heart disease. Additionally, general people can take care of their health based on the critical factors to avoid heart diseases. So, our target audience will be benefited by this analysis to know about their health conditions and the key factors that might be at risk for heart diseases.

### Challenges

The correlation between each factors present the dataset to the heart disease is less and in turn the precision for true positive scenario is almost negligible. Hence obtaining a good accuracy of the model was very challenging. That is why the probability estimation may not correlate well in real life. Implementing the validation scenarios for the user input parameters had to be done with precision. Understanding the underlying concepts of newton’s method was challenging. 

### Personal Learning

By working on this project, we have learnt how to develop a logistic regression model for estimating probability of heart diseases based on different health conditions of a person. We have learnt how to use excel and VBA to develop the model. We have also learnt how to organize and pre-process data and use that to analyze and develop models. Additionally, we have learnt how to deal with poor data in real life. 

### Closing Thoughts

The future scope of this project will be to use advanced analytical models and tools to achieve better accuracy. This robust model can be a great help for medical teams, patients, and general people to be aware of the key factors causing heart diseases so that precautions can be taken to avoid it. Additionally, this study will help the government's health department to know about the statistics of heart diseases that can be promoted for awareness. Our userform will help anyone to know whether they are prone to heart disease or not when they put in their health and lifestyle information.

### Reference 

•	Wikipedia Contributors. (2021, October 12). Newton’s method in optimization. Wikipedia; Wikimedia Foundation. https://en.wikipedia.org/wiki/Newton%27s_method_in_optimization

•	Luca, G. D. (2020, September 16). Gradient Descent vs. Newton’s Gradient Descent | Baeldung on Computer Science. Www.baeldung.com. https://www.baeldung.com/cs/gradient-descent-vs-newtons-gradient-descent

•	Excel Solver: Which Solving Method Should I Choose? (2016, November 29). EngineerExcel. https://engineerexcel.com/excel-solver-solving-method-choose/
