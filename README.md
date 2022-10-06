# MBA_ISDE2021-22_CAPSTONE_CREDIT_CARD_DEFAULTER
To build a classification methodology to determine whether a person defaults the credit card payment for the next month. 

## Start CAPSTONE - ML - PROJECT 

We will build a machine learning project and deploy to cloud environment. 
We will get an API and we will do the predictions.
Different sections in the project

1. Problem statement
    What is the problem given to us by the client.
2. Description of the data
    What is the data given to us by the client.
    What will be the individual columns and what will be the target columns.
    What is the meaning of the individual columns.
3. Application architechture and module division
    What will be the modules.
    Divide the bigger problems into smaller modules and solve it.
4. Code Explanation
   After having the theoretical background of the prblem we will go with the coding. Various steps involved in the coding are as follows. 
   # a. Data Ingestion
   We will get the data from the client using the mechanism listener to read the data from the topic/database or file poling as suggested by the client or as per the agreement.
   Once we get the data then we check the details of the data or do the validation of the data weather it is as per the agreement by the client. If it is as per the client requirements we will accept the data and put it forward for data preprocessing if not we reject the data and put it in a different folder. 

   # b. Data Preprocessing
   Data cleaning weather the data is 
   i.  normally distributed or not
   ii. how to fill the missing values
   iii.hot to convert the categorical variable to non categorical variable
   iv. if there is any imbalance in the data how to overcome the imbalance in the data over sampling or under sampling
   So whatever techniques is required to clean the data we will use it and perform the same in data preprocessing.

   # c. Model Selection
   Once the data is preprcessed we will diving the data into clusters and apply models on the clusters.
   e.g. one one cluster XG boost , other cluster gradient boost etc.
   After that we go for model tuning.

   # d. Model Tuning
   Out of all these models we will go for hyper parameter tuning and will go for the best model for the particular cluster.
   And we saved the particular model.
   After that we go for the prediction.

   # e. Prediction 
   After we select the model we go for the predictions based on the model we have saved. 
   Again all the data preprocessing steps have to be performed again that we dont during the training.
   Once the data is preprocessed again we will pass it to the clustering algorithm and we will predict the cluster number to which cluster a particular row below after that we will select the ML model for that particular cluster using that model we will do the prediction and then we will combine all the predictions and put it in to a csv file or save it to a file location from where the client can pole or you can post it to a stream we can go as per the client requirements.

   # f. Logging Framework
   Whatever we are doing all the operation should be logged. 
   So that we can keep track of the steps.

   # g. Deployment
   Once all the coding is done we will go for the cloud deployement and shared the API link to the client. 










### Software and Account requirements

Creating conda environment

```
conda create -p venv python==3.7 -y

```
conda activate venv/
```
OR 
```
conda activate venv
```
```
pip install -r requirements.txt
```

To Add files to git
```
git add .
```

OR
```
git add <file_name>
```



To install latest version of pandas 
```

```


> Note: To ignore file or folder from git we can write name of file/folder in .gitignore file

To check the git status 
```
git status
```
To check all version maintained by git
```
git log
```

To create version/commit all changes by git
```
git commit -m "message"
```
To send version/changes to github
```
git push origin main

and 

git push to update the pending branch

To install latest version of pandas

```

conda install pandas

```


```


```
about main.py
it consists of 3 routes
# homepage
# training 
# prediction 
```

LOGGING OF THE FILE
```
We need to login each and every step. 
So that the support team has better ease of access of our application.
For erroneous situation and exception.
Easy to locate when it was failed and what time it was failed and which file caused the failure.

We have use applicaiton_logging folder to log the file in which logger.py python coding is done


Several ways to perform logging 
# 1. Logs to a file 
# 2. Logs to a database
# 3. Logs to a topic ( listner and consumer will be listening) etc.
# 4. Custom logging framework

In this project we will be writing our own custom framework.

```


VALIDATION AND TRANSFORMATION

```
Validation: Here we have to check weather the data which have been sent to us by the client is valid or not.
We will check our constraints and if the validation rule pass we will put the data into good raw data folder and if the constrains failed we will put it into bad raw data folder (archieved).

From the good raw data folder we will put it into the database and convert it into a form of table.
And then we will export the csv file as an input for the training data

It will be a json file either given by the client or you can create by your own after discussing with the client.
e.g. schema_training.json

Various constraints taken in the project are :
1. Length of the file
2. Check any missing values
3. Length of the column

TRANSFORMATION:

for e.g. sql does not understand the NAN values it understands the NULL values so that type of transformation has been done.
 
```

DB Operation

```
GOOD RAW DATA FOLDER AND BAD RAW DATA FOLDER ARE THE temporary FOLDERS JUST FOR INSERTION AND DELETION OF THE FILES

```

DATA PREPROCESSING:

```
Validated and Transformed data is moved to the Folder Training_FileFromDB from the database.
We retrieve the data in the form of a csv file and then we do the preprocessing.
Before we send the file for modeling we do the following steps in data preprocessing:

1. Remove unwanted space from the file

2. Remove columns

3. Separate label features

4. Check for null presence

5. Missing value imputation 

6. Scaling

7. Encode categorical columns

8. Handle imbalance datasheet


```

CLUSTERING

```
Once the data is preprocessed and cleaned. 
Now next step is clustering. Why clustering ?
Support we have a data distribution and we perform a linear regression on the data and we get the one best fit line and calculate the sum of residuals on that best fit line suppose that is R1.

Now if we divide the same data into clusters and perform linear regression on that data with multiple best fit lines in the distributed data and then caluclate the value of sum of residuals e.g. R2+R3+...+Rn = Rd.

So the value of Rd < R1 .

So the less value of the residuals better is the performance after we apply machine learning models on each clusters.


NOW WHICH CLUSTERING APPROACH TO FOLLOW?

We will be using the k means clustering. 
And in order to get the best value of k there are two methds:

a. Elbow method.

b. Kneed library. 


After we get the optimum no. of clusters. 

We have to create those clusters. Separate columns will be created for the clusters.

And then we have to label those columns in group.

cluster 0 = group 0
cluster 1 = group 1 
cluster 2 = group 2 
.
.
.
cluster n = group n 
where n is the optimum number of clusters. 

And then we will apply the machine learning models on the groups and do the hypertuning of the models so that we can get the best ML models

```
MODEL SELECTION AND MODEL TUNING

```
As this is the classification model we can either go any clssification models from the market.
like: 
Various classification models are: 

1. Logistic regression.
2. Decision tress.
3. Random Forest
4. SVM
5. Naive Bayes
6. KNN
7. XG Boost
etc. 



# PREDICTION
```

Similar process will be used for the data predicton which was used for training data.
Read client data
Data Validation and Training 
DB Operations
csv - input for predicitons
Data preprocessing
Clustering
Now we have to cluster number for individuals rows
Load cluster models
Predictions and move it in a csv file.
```

# DEPLOYMENT

```
Need to add two files.

1. requirements.txt
Here in this various libraries and modules which are required to run the appoications

2. Procfile
which file it starts running first

web:gunicorn main: app

web: It is a web application
gunicorn: Web Service Gateway Interface(WSGI) more request from web server to your application and vice-versa

main: name of the file to be executed first

app: name of the app use in this project we have used flask


After the above steps are completed.

CLOUD DEPLOYMENT:

•	Go to Heroku.com and create an account and login.
•	Click on new(inside the red box) to create a new app.
•	Give the name of the app and click ‘create app’.
•	After app creation, the ‘deploy’ section has all the deployment steps mentioned.
•	We’ll download and install the Heroku CLI from the Heroku website: https://devcenter.heroku.com/articles/heroku-cli.
•	Git also needs to be installed in your computer
•	After installing the Heroku CLI, Open a command prompt window and navigate to your project folder.
•	Type the command ‘heroku login’ to login to your heroku account
•	Before deploying the code to the Heroku cloud, we need to commit the changes to the local git repository.
•	Type the command ‘git init to initialize a local git repository
•	Enter the command heroku git:remote <remote repo name> to connect local git repo to the remote repo.
•	Enter the command ‘git status’ to see the uncommitted changes
•	Enter the command ‘git add .’ to add the uncommitted changes to the local repository.
•	Enter the command ‘git commit -am "make it better"’ to commit the changes to the local repository.
•	Enter the command ‘git push heroku master’ to push the code to the heroku cloud.
•	After deployment, heroku gives you the URL to hit the web API.
Once your application is deployed successfully, enter the command ‘heroku logs --tail’ to see the logs.


```

