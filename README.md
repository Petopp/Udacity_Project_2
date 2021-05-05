
# Udacity Machinelearning Project 2 for Machine Learning Engineer with Microsoft Azure.

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

## 1. Loading the CSV to the Dataset
The download path was communicated at the beginning of the project. 
This was then downloaded and imported into the dataset. The steps are identical to those carried out in project 1.

Here can you see, the result of loading the files in the Dataset

![image](https://user-images.githubusercontent.com/41972011/117182580-cda9dc80-add6-11eb-8bdf-2fcfd5796c82.png)

and here can you see the confirmation from Azure

![image](https://user-images.githubusercontent.com/41972011/117182190-583e0c00-add6-11eb-975c-916fdc64ff29.png)



## 2. AutoML - setup: 
In the next steps we are defining the compute cluster and starting the experiment


![image](https://user-images.githubusercontent.com/41972011/117183622-0a2a0800-add8-11eb-9ac9-b18e25772d81.png)

![image](https://user-images.githubusercontent.com/41972011/117182858-2a0cfc00-add7-11eb-979c-849eb47e147a.png)

AUTOML-experiment is completed:

![image](https://user-images.githubusercontent.com/41972011/117183691-2037c880-add8-11eb-8a99-654dd12624e5.png)






Best model is VotingEnsemble with Accuracy of 0.91897


## 2. Deployment of best model

In the pictures below, we see that we have delpoyed the best model chosen from AutoML and enabled the following:
- REST endpoint with Key-based authentification



## 3. Enable logging

This step shows that Application Insights is enabled.


Screenshot from logs.py:


## 4. Swagger & endpoint consumption 

Furthermore, we have also testet the API with swagger using sample data. Swagger is a very handy too, in oder to easily test REST-APIs. Azure provides a swagger.json file to easly test the deployed models-API.

In addition to that, we have also testet the endpoint by running the endpoint.py Python-file. The result of the test can be seen as the output of the Python-Script below:


## 5. Publish the Pipeline

Pipelines - general view

![image](https://user-images.githubusercontent.com/81966908/116793319-6cc49080-aac6-11eb-98dc-4f21cea7c583.png)


Pipeline - Endpoints 

![image](https://user-images.githubusercontent.com/81966908/116793390-d2b11800-aac6-11eb-8e85-f34aca41da39.png)

Pipeline - REST-endpoint
![image](https://user-images.githubusercontent.com/81966908/117018550-e215a880-acf4-11eb-85b4-0c75c23f985d.png)

Pipleine - Completet status of Pipeline
![image](https://user-images.githubusercontent.com/81966908/117018656-ffe30d80-acf4-11eb-959a-66b70b1d1758.png)


Pipelines - overview showing:
  - general info
  - REST-Endpoint
  - interaction AutoML and dataset

![image](https://user-images.githubusercontent.com/81966908/116793490-523ee700-aac7-11eb-87f4-addd81fdf7f5.png)

Screenshot of RunDetails widgets

![image](https://user-images.githubusercontent.com/81966908/116887413-926aaa80-ac2a-11eb-9646-41b43f6b3838.png)

Jupyter - published pipline

![image](https://user-images.githubusercontent.com/81966908/116887637-cfcf3800-ac2a-11eb-8863-35311a096bb3.png)

Jupyter - Pipelineendpoint test succesfull

![image](https://user-images.githubusercontent.com/81966908/117019360-9fa09b80-acf5-11eb-9ef5-1f08ccb15f2d.png)

testing endpoint with pyhton endpoint.py file -> successfull
![image](https://user-images.githubusercontent.com/81966908/117020109-6b79aa80-acf6-11eb-851b-de4a2f62360b.png)



Jupyter - Modeldetails
![image](https://user-images.githubusercontent.com/81966908/116888138-656ac780-ac2b-11eb-9023-58b0d7b582a8.png)



## Screen Recording

https://youtu.be/RA1q-109xOU

## Suggestions for Improvement

1. I would use a longer compute-period/time-frame to get a higher accuracy and give the AutoMLarlgorithms more time to fine tune the results
2. I would also enable the Deep Learning funtionality, to try out NN-based algorithms (requires GPU enabled compute-resource)
3. I would also try to get a bigger dataset or maybe amend the dataset, since I think it might be biased, given that there are many differnt Columns/features, which could lead to unbalanced sub-groups
