# Udacity Machine Learning Project 2 for Machine Learning Engineer with Microsoft Azure.

In this project we focused more to the Endpoints and SDK in Azure Machine Learning. To do this, we used the MS Azure Machine Learning Studio to run a AutoML-algorithm, which fits to the already used Bank Marketing Dataset from Project 1. Furthermore, we made it ready for production and deployed it using ACI (Azure Container Instance). The trained model is consumend via REST-API (http-request). Also a pipline was build and consumed.


## Summary of the procedure

1.  Download the CSV file of Bank Marketing Data. (You can find the file in this project folder)

2.  Uploaded this file to Azure Machine Learning in to a dataset. 

    -In the AutoML functionality, we have defined that the problem we want to tackle is a classification. We have also defined that the variable y (which refers to the decision      whether a customer is eligible or not) is our target variable (binary variable).

3.  Then a compute-cluster was generated ("Standard-DS12_v2").

4.  Through Azure Auto ML functionality, we found the best model and deployed it with ACI (the algorithm with the name "voting ensemble" was the best in this test)

5.  Logging and Appplication Insights have been enabled to provide information about the requirements and performance related to the model in use.

6.  The Rest endpoint was testet for connectivity (over Swagger)

7.  Finally step, we used the python SDK to generate a pipleine and published it.


## Key Steps

### 1. Loading the CSV to the Dataset
The download path was communicated at the beginning of the project. 
This was then downloaded and imported into the dataset. The steps are identical to those carried out in project 1.

Here can you see, the result of loading the files in the Dataset

<kbd>![image](https://user-images.githubusercontent.com/41972011/117182580-cda9dc80-add6-11eb-8bdf-2fcfd5796c82.png)</kbd>

and here can you see the confirmation from Azure

<kbd>![image](https://user-images.githubusercontent.com/41972011/117182190-583e0c00-add6-11eb-975c-916fdc64ff29.png)</kbd>


### 2. AutoML - setup: 
In the next steps we are defining the compute cluster and starting the experiment

Start and configuration the experiment:

<kbd>![image](https://user-images.githubusercontent.com/41972011/117183622-0a2a0800-add8-11eb-9ac9-b18e25772d81.png)</kbd>

<kbd>![image](https://user-images.githubusercontent.com/41972011/117182858-2a0cfc00-add7-11eb-979c-849eb47e147a.png)</kbd>

AUTO ML-experiment is now completed:

<kbd>![image](https://user-images.githubusercontent.com/41972011/117183939-6ee56280-add8-11eb-8633-d6594c959316.png)</kbd>

<kbd>![image](https://user-images.githubusercontent.com/41972011/117183959-79076100-add8-11eb-8da9-d9d78f73f61f.png)</kbd>

Best model is VotingEnsemble with Accuracy of 0.92018 in this experiment.

<kbd>![image](https://user-images.githubusercontent.com/41972011/117184106-a6540f00-add8-11eb-82dd-5d9f96191dc2.png)</kbd>

Here you can see the calibration curve of this model. The calibration curve represents the confidence of a model in terms of its predictions compared to the proportion of positive samples at the respective confidence levels. [Here](https://docs.microsoft.com/de-de/azure/machine-learning/how-to-understand-automated-ml#calibration-curve) can you find more information over this.

<kbd>![image](https://user-images.githubusercontent.com/41972011/117184268-d4395380-add8-11eb-835b-ef9cfd3eac8e.png)</kbd>

As well as an overview of the results of other algorithms.

<kbd>![image](https://user-images.githubusercontent.com/41972011/117184374-f206b880-add8-11eb-8eab-1ccf79ad202f.png)</kbd>


### 2. Deployment of best model

Here you can see that the best model from AutoML has been selected and the authenficartion has been activated. The computer type was also set to ACI as required.

<kbd>![image](https://user-images.githubusercontent.com/41972011/117184434-05b21f00-add9-11eb-9f50-8f5cace9737b.png)</kbd>

Here is the status that the model now has

<kbd>![image](https://user-images.githubusercontent.com/41972011/117184699-4ca01480-add9-11eb-983a-a3b2c0031fa6.png)</kbd>


### 3. Enable logging

As seen above, I chose the best model (VotingEnseble) for deployment and enable "Authentication" as well as the computer tpye Azure Container Instance (ACI). 
The code executed here in logs.py enables "Application Insights". "Application Insights enabled" was disabled before logs.py was executed.

Here the result in the Python Shell

<kbd>![image](https://user-images.githubusercontent.com/41972011/117184945-97219100-add9-11eb-98d7-686dfef9ce21.png)</kbd>

and in Azure

<kbd>![image](https://user-images.githubusercontent.com/41972011/117184987-a4d71680-add9-11eb-9a43-eb98ad07d1bf.png)</kbd>


### 4. Swagger & endpoint consumption 

We also tested the API with Swagger using sample data. 
Swagger is also a very practical tool to easily test REST APIs. Azure provides a swagger.json file to easily test the provided models API and to address the trained models via a program.

This is the web interface of swagger, with "connect" to the jason file from the model

<kbd>![image](https://user-images.githubusercontent.com/41972011/117185368-0d25f800-adda-11eb-8a80-c5107106da37.png)</kbd>

and here is a example for communication with the model

<kbd>![image](https://user-images.githubusercontent.com/41972011/117185420-1c0caa80-adda-11eb-8372-f89a7f6b393e.png)</kbd>

 we have also testet the endpoint by running the endpoint.py Python-file.
 The result of the test can be seen as the output of the Python-Script below:

<kbd>![image](https://user-images.githubusercontent.com/41972011/117188022-db626080-addc-11eb-8805-e2e62853976c.png)</kbd>


### 5. Overview over the Pipeline (it's more FYI)

Pipelines - general view

<kbd>![image](https://user-images.githubusercontent.com/41972011/117185933-a6eda500-adda-11eb-9ff2-44cab633334b.png)</kbd>

Pipeline - Endpoints 

<kbd>![image](https://user-images.githubusercontent.com/41972011/117185954-abb25900-adda-11eb-8f2e-02f3ad3a339e.png)</kbd>

Pipeline - REST-endpoint
<kbd>![image](https://user-images.githubusercontent.com/41972011/117186105-ce447200-adda-11eb-98e1-0151833e9016.png)</kbd>


### 6. Runnig the SDK over Jupyter

After upload the Jupyter programm in to Azure, can you find this on this file here:

<kbd>![image](https://user-images.githubusercontent.com/41972011/117186452-211e2980-addb-11eb-8d9b-70fdcc6ddcea.png)</kbd>

Running the experiment over SDK

<kbd>![image](https://user-images.githubusercontent.com/41972011/117329455-f1cbf300-ae94-11eb-930f-d69989d6445c.png)</kbd>

<kbd>![image](https://user-images.githubusercontent.com/41972011/117186816-8114d000-addb-11eb-9376-a10f3d58ce2c.png)</kbd>

<kbd>![image](https://user-images.githubusercontent.com/41972011/117186860-8eca5580-addb-11eb-9525-178cfedf2ae9.png)</kbd>

Message that it is finished

<kbd>![image](https://user-images.githubusercontent.com/41972011/117186616-4dd24100-addb-11eb-9ddc-507a517c2f1e.png)</kbd>

Aceess to the REST Endpoint over Jupyter:

<kbd>![image](https://user-images.githubusercontent.com/41972011/117187338-1a43e680-addc-11eb-91cf-90b6107e6a64.png)</kbd>

Or you can see the url to the REST API here together with the published pipeline:

<kbd>![image](https://user-images.githubusercontent.com/41972011/117187632-6a22ad80-addc-11eb-8e21-bfc3c3976c22.png)</kbd>

And a final test over python

<kbd>![image](https://user-images.githubusercontent.com/41972011/117187831-a35b1d80-addc-11eb-945d-30c3ceb70ed7.png)</kbd>

with the best algorithm 

<kbd>![image](https://user-images.githubusercontent.com/41972011/117188267-2c725480-addd-11eb-9df4-e86533259064.png)</kbd>


## Recording
[YouTube](https://youtu.be/JpwZw998Xgk)


## Suggestions for improvement for future experiments
1.  I will use by repating this a longer computation period/time frame  to get higher accuracy and give the AutoML arlgorithms more time to fine-tune.

2.  Also enable Deep Learning functionality to try NN-based algorithms (requires GPU-capable computational resources). This could yield better results, provided that 
    the amount of data can be increased as listed in point 3 in a moment.

3.  I would try to get a larger data set, possibly from other regions/countries. 
    Since data from only one specific region could also bias the algorithm if it were to be used elsewhere.
