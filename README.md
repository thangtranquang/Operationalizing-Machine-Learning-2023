# Operationalizing Machine Learning - Thang Tran

## Table of Content

* [Project Overview](#overview)
* [Architectural Diagram](#architectural-diagram)
* [Key Steps](#architectural-diagram)
  * [Authentication](#authentication)
  * [Automated ML Experiment](#automated-ml-experiment)
  * [Deploy the best model](#deploy-the-best-model)
  * [Enable logging](#enable-logging)
  * [Swagger Documentation](#swagger-documentation)
  * [Consume model endpoints](#consume-model-endpoints)
  * [Create and publish a pipeline](#create-and-publish-a-pipeline)
* [Screen Recording](#screen-recording)
* [Standout Suggestions](#standout-suggestions)

## Project Overview

In this project, you will continue to work with the [Bank Marketing dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv). We will use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. We will also create, publish, and consume a pipeline. In the end, you will demonstrate all of your work by creating a README file and a screencast video.

## Architectural Diagram



![515a0e29-e926-42ef-865a-d8666c3b8118](file:///C:/Users/tranqt07/Pictures/Typedown/515a0e29-e926-42ef-865a-d8666c3b8118.png)



## Key Steps

### Authentication

az login

![c45286b7-a1e5-4eb1-bbae-da53a5b931e5](file:///C:/Users/tranqt07/Pictures/Typedown/c45286b7-a1e5-4eb1-bbae-da53a5b931e5.png)

### Automated ML Experiment

- In this step, I created an AutoML experiment to run using the [Bank Marketing](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv) Dataset which was loaded in the Azure Workspace, choosing **'y'** as the target column.

![0c8504bb-3b3e-45e9-a7ec-dc380173b20d](file:///C:/Users/tranqt07/Pictures/Typedown/0c8504bb-3b3e-45e9-a7ec-dc380173b20d.png)



- Create new Automated ML
  
  

![513221e8-916c-40fd-809c-e3a3be927e2d](file:///C:/Users/tranqt07/Pictures/Typedown/513221e8-916c-40fd-809c-e3a3be927e2d.png)







![66a34d2b-98c0-47be-88cf-8b7ee9bd2a23](file:///C:/Users/tranqt07/Pictures/Typedown/66a34d2b-98c0-47be-88cf-8b7ee9bd2a23.png)

![382c9e30-dcdd-4d92-87f0-90919d10255e](file:///C:/Users/tranqt07/Pictures/Typedown/382c9e30-dcdd-4d92-87f0-90919d10255e.png)

- Run the experiment using Classification

![702ee14d-0e49-4b18-b61a-e5ace65572e9](file:///C:/Users/tranqt07/Pictures/Typedown/702ee14d-0e49-4b18-b61a-e5ace65572e9.png)

- The experiment is running, and many models are being trained on the **Bank Marketing** Dataset to find the best one.

![3f47bf97-fa14-4013-9062-8440d70a8bb8](file:///C:/Users/tranqt07/Pictures/Typedown/3f47bf97-fa14-4013-9062-8440d70a8bb8.png)

After a while, the eperiment is complete and I can access the models that were trained and find the best model.

The best model for this classification problem was a **Voting Ensemble** model with **0.94769** Accuracy.

![fc7b4ab5-554f-43b7-a746-f31f8f5ef5a0](file:///C:/Users/tranqt07/Pictures/Typedown/fc7b4ab5-554f-43b7-a746-f31f8f5ef5a0.png)



![d2a86de2-13a9-4afb-ac35-4f49535c6bef](file:///C:/Users/tranqt07/Pictures/Typedown/d2a86de2-13a9-4afb-ac35-4f49535c6bef.png)

I access the best model to learn more about its metrics and other details.

![70eb222f-694a-4152-af41-268da0f7ca7b](file:///C:/Users/tranqt07/Pictures/Typedown/70eb222f-694a-4152-af41-268da0f7ca7b.png)

![c96d744b-45c2-43a0-aacd-7683d60763ee](file:///C:/Users/tranqt07/Pictures/Typedown/c96d744b-45c2-43a0-aacd-7683d60763ee.png)

In this section, I can see all of the model's metrics, such as *Accuracy*.

![d311ea69-ce90-4585-bb86-9c29c94702a5](file:///C:/Users/tranqt07/Pictures/Typedown/d311ea69-ce90-4585-bb86-9c29c94702a5.png)



![77b995e8-2f97-40ba-8fdf-0c543b55ba4b](file:///C:/Users/tranqt07/Pictures/Typedown/77b995e8-2f97-40ba-8fdf-0c543b55ba4b.png)



![0279a85f-400e-49a5-9cd0-344428ebc3f1](file:///C:/Users/tranqt07/Pictures/Typedown/0279a85f-400e-49a5-9cd0-344428ebc3f1.png)

### Deploy the best model

Use the best chosen model for our task, we need to deploy it.  we deployed our trained Voting Ensemble model using Azure Container Instance (ACI), with authentication enabled.

![6ed30c06-8b0a-4f8e-b0ea-66330b54748f](file:///C:/Users/tranqt07/Pictures/Typedown/6ed30c06-8b0a-4f8e-b0ea-66330b54748f.png)

![b79654ba-e71b-4242-a91e-87964cbb1b8e](file:///C:/Users/tranqt07/Pictures/Typedown/b79654ba-e71b-4242-a91e-87964cbb1b8e.png)

### Enable logging

Running the logs.py script requires interactive authentication, after successfully logging in

![5a609708-3c19-4b77-9042-5573a21a14c6](file:///C:/Users/tranqt07/Pictures/Typedown/5a609708-3c19-4b77-9042-5573a21a14c6.png)

![24b2438b-041b-40f3-beea-e350f7f3376c](file:///C:/Users/tranqt07/Pictures/Typedown/24b2438b-041b-40f3-beea-e350f7f3376c.png)



By running the logs.py script, we enable *Application Insight*.

![b1475b59-61d7-4af0-8888-0687093431c7](file:///C:/Users/tranqt07/Pictures/Typedown/b1475b59-61d7-4af0-8888-0687093431c7.png)

### Swagger Documentation

Download the **swagger.json** file provided to us in the Endpoints section of Azure Machine Learning Studio.

Then we run the **swagger.sh** and **serve.py** files to be able to interact with the swagger instance running with the documentation for the HTTP API of the model.

![97851af7-da45-4538-b9cd-6b41a8d5ddb2](file:///C:/Users/tranqt07/Pictures/Typedown/97851af7-da45-4538-b9cd-6b41a8d5ddb2.png)

### Consume model endpoints

Run the **endpoint.py** script to show the **scoring_uri** and the **key** 



![c380abb5-abd4-4ebb-b7dc-909c5e471f5b](file:///C:/Users/tranqt07/Pictures/Typedown/c380abb5-abd4-4ebb-b7dc-909c5e471f5b.png)

#### Benchmark

![d67c7dd6-f59f-432f-9fbd-00a969c003e5](file:///C:/Users/tranqt07/Pictures/Typedown/d67c7dd6-f59f-432f-9fbd-00a969c003e5.png)

Results of load-testing our deployed model.

![e06f7f9a-676d-487f-b3dc-6c1c76cc1a80](file:///C:/Users/tranqt07/Pictures/Typedown/e06f7f9a-676d-487f-b3dc-6c1c76cc1a80.png)



### Create and publish a pipeline

Create a Pipeline in the SDK

![90bd1f13-a8ab-445b-83ac-38d68bed2e24](file:///C:/Users/tranqt07/Pictures/Typedown/90bd1f13-a8ab-445b-83ac-38d68bed2e24.png)

This is the pipeline created in the *Pipelines* section of Azure ML Studio

![e78f60ae-180f-4cad-85c2-517dca1a8628](file:///C:/Users/tranqt07/Pictures/Typedown/e78f60ae-180f-4cad-85c2-517dca1a8628.png)



![c73b42c8-6284-471a-b4be-ea66cb4c8e41](file:///C:/Users/tranqt07/Pictures/Typedown/c73b42c8-6284-471a-b4be-ea66cb4c8e41.png)





## Screen Recording

[Video Link](https://drive.google.com/file/d/1mHkeDEZ0JDpS-0Q5Ax1ooIWWqpbcWd6E/view?usp=drive_link)

<!--[Subtitles](https://drive.google.com/file/d/1urtaKvpkmQr-1t5N8SGM42FD4NZKKts_/view?usp=sharing)-->

## Standout Suggestions

When creating an AutoML run was the imbalanced data issue => This can lead to biased prediction, which can affect negatively the model's accuracy. 


