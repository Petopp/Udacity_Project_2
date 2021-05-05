
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

Start and configuration the experiment:

![image](https://user-images.githubusercontent.com/41972011/117183622-0a2a0800-add8-11eb-9ac9-b18e25772d81.png)

![image](https://user-images.githubusercontent.com/41972011/117182858-2a0cfc00-add7-11eb-979c-849eb47e147a.png)

AUTOML-experiment is completed:

![image](https://user-images.githubusercontent.com/41972011/117183939-6ee56280-add8-11eb-8633-d6594c959316.png)

![image](https://user-images.githubusercontent.com/41972011/117183959-79076100-add8-11eb-8da9-d9d78f73f61f.png)


Best model is VotingEnsemble with Accuracy of 0.92018

![image](https://user-images.githubusercontent.com/41972011/117184106-a6540f00-add8-11eb-82dd-5d9f96191dc2.png)

Here are graphical evaluations showing the distribution and calculations in this model.

![image](https://user-images.githubusercontent.com/41972011/117184268-d4395380-add8-11eb-835b-ef9cfd3eac8e.png)

![image](https://user-images.githubusercontent.com/41972011/117184299-dbf8f800-add8-11eb-98c5-805e1e08bf7a.png)

As well as an overview of the results of other algorithms.

![image](https://user-images.githubusercontent.com/41972011/117184374-f206b880-add8-11eb-8eab-1ccf79ad202f.png)


## 2. Deployment of best model

Here you can see that the best model from AutoML has been selected and the authenficartion has been activated. The computer type was also set to ACI as required.

![image](https://user-images.githubusercontent.com/41972011/117184434-05b21f00-add9-11eb-9f50-8f5cace9737b.png)

Here is the status that the model now has

![image](https://user-images.githubusercontent.com/41972011/117184699-4ca01480-add9-11eb-983a-a3b2c0031fa6.png)


## 3. Enable logging

Now we activate the Application Insights over the logs.py programm. Here can we see the results of this

in the Python Shell

![image](https://user-images.githubusercontent.com/41972011/117184945-97219100-add9-11eb-98d7-686dfef9ce21.png)

and in Azure

![image](https://user-images.githubusercontent.com/41972011/117184987-a4d71680-add9-11eb-9a43-eb98ad07d1bf.png)



## 4. Swagger & endpoint consumption 

We also tested the API with Swagger using sample data. 
Swagger is also a very practical tool to easily test REST APIs. Azure provides a swagger.json file to easily test the provided models API and to address the trained models via a program.

This is the web interface of swagger, with "connect" to the jason file from the model

![image](https://user-images.githubusercontent.com/41972011/117185368-0d25f800-adda-11eb-8a80-c5107106da37.png)

and here is a example for communication with the model

![image](https://user-images.githubusercontent.com/41972011/117185420-1c0caa80-adda-11eb-8372-f89a7f6b393e.png)


Final in this step, we are testing the enpoint.py Python programm the coummincation.

![image](https://user-images.githubusercontent.com/41972011/117185603-4e1e0c80-adda-11eb-9336-82695084f1fe.png)





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
