# Operationalizing Machine Learning #


This is second project in the Udacity nanodegree - "Machine Learning Engineer with Microsoft Azure". The aim of this project is to configure a cloud-based machine learning production model, deploy it, and consume it. Along with it - create, publish, and consume a pipeline.

The dataset used here is same as used in Project 1 which was about bank marketing, which had 32950 rows and 21 columns - age,job,marital,education,default,housing,loan,contact,month,day_of_week,duration,campaign,pdays,previous,poutcome,emp.var.rate,cons.price.idx,cons.conf.idx,euribor3m,nr.employed and y.

Our target column name is "y" in which entries are - 'yes' and 'no'.

We will be using Azure ML Studio as well as Python SDK to complete this project. 

- - - -

## Architectural Diagram ##

Mainly the project has 7 steps, 8th one is documenttion which is needed for submission of the project. 

![3](https://user-images.githubusercontent.com/34343621/115155839-40a91880-a09f-11eb-8ba4-7dc7069f2d5a.png)

So here are all the steps:

1. Authentication
2. Automated ML Experiment
3. Deploy the best model
4. Enable logging
5. Swagger Documentation
6. Consume model endpoints
7. Create and publish a pipeline
8. Documentation

### 1. Authentication ###
As I used Udacity lab itslef, there was no need for me to perform this step. The goal of this step is: to install the Azure Machine Learning Extension which allows you to interact with Azure Machine Learning Studio, part of the az command. After having the Azure machine Learning Extension, to create a Service Principal account and associate it with your specific workspace.


### 2. Automated ML Experiment ###
In this step, one has to create an experiment using Automated ML, configure a compute cluster, and use that cluster to run the experiment.


### 3. Deploy the best model ###
After the experiment run completes, a summary of all the models and their metrics are shown, including explanations. The Best Model will be shown in the Details tab. In the Models tab, it will come up first (at the top)

### 4. Enable logging ### 
Now that the Best Model is deployed, enable Application Insights and retrieve logs. Although this is configurable at deploy time with a check-box, it is useful to be able to run code that will enable it for one.

### 5. Swagger Documentation ###
In this step, one has to consume the deployed model using Swagger.

### 6. Consume model endpoints ###
Once the model is deployed, use the endpoint.py script provided to interact with the trained model. In this step, one is needed to run the script, modifying both the scoring_uri and the key to match the key for your service and the URI that was generated after deployment.

### 7. Create and publish a pipeline ###
For this part of the project, one has to use the Jupyter Notebook provided in the starter files, also make sure to update the notebook to have the same keys, URI, dataset, cluster, and model names already created.

## Key Steps ##
1. There needs a dataset present for us to work with, so we need to confirm if dataset is present. Here we can see the dataset. 
![1](https://user-images.githubusercontent.com/34343621/115162401-f33da300-a0c0-11eb-834d-0e758cfa145a.png)

Next thing to do is feed it to AutoML, after fixing the target coloum which in our case was y and Classification is method used by AutoML
![2](https://user-images.githubusercontent.com/34343621/115162442-241dd800-a0c1-11eb-92aa-44741be5a607.png)

It takes some mintues to run it complete, once it ran complete it was clear that best algorithm was VotingEnsemble with accuracy of 91.8%.
![3](https://user-images.githubusercontent.com/34343621/115162573-fe450300-a0c1-11eb-89fa-dcaae3458ca3.png)
![4](https://user-images.githubusercontent.com/34343621/115162574-01d88a00-a0c2-11eb-820d-6bac4cf24a05.png)
![5](https://user-images.githubusercontent.com/34343621/115162588-1452c380-a0c2-11eb-9ee6-6716ae1d0c2f.png)
![6](https://user-images.githubusercontent.com/34343621/115162725-ab1f8000-a0c2-11eb-8291-599f41e17955.png)


2. We then deploy the model with ACI and Enable authentication. 
![7](https://user-images.githubusercontent.com/34343621/115162673-77dcf100-a0c2-11eb-820a-78589ffd45e0.png)

Deployment has started in this screenshot. 
![8](https://user-images.githubusercontent.com/34343621/115163446-cd1b0180-a0c6-11eb-8a13-f2d681bc858b.png)

3.  Enable Log insights by running log.py file.  
![8 1](https://user-images.githubusercontent.com/34343621/115163624-c214a100-a0c7-11eb-95e8-92f5432544b5.png)

After running log.py we can see insights
![9](https://user-images.githubusercontent.com/34343621/115163512-1f5c2280-a0c7-11eb-8cff-c00c14ffd2f1.png)
![10](https://user-images.githubusercontent.com/34343621/115163680-1ae43980-a0c8-11eb-8b37-5b7d5bf897d6.png)
![11](https://user-images.githubusercontent.com/34343621/115163683-1ddf2a00-a0c8-11eb-8d93-a6fac602012b.png)

This is dashboard of insights. 
![9 1](https://user-images.githubusercontent.com/34343621/115163505-12d7ca00-a0c7-11eb-932b-435678941cb2.png)

4. Make documentation of deployed endpoint using swagger: We need swagger.json file which we download and keep it along with other swagger files. Then we execute swaager.sh file to get our swagger dashboard. 
![12](https://user-images.githubusercontent.com/34343621/115163686-26cffb80-a0c8-11eb-8a17-2f6ac88f2320.png)

 ![13](https://user-images.githubusercontent.com/34343621/115163715-4a934180-a0c8-11eb-918a-a9619352ebd1.png)

We run serve.py, to see our requests. 
![14](https://user-images.githubusercontent.com/34343621/115163744-6bf42d80-a0c8-11eb-8f67-f20c54888162.png)
![15](https://user-images.githubusercontent.com/34343621/115163750-71ea0e80-a0c8-11eb-89a6-c01d107c1337.png)

5. Consume the model endpoints - we make changes to endpoint.py file - we provide it with scoring_uri and key
![16](https://user-images.githubusercontent.com/34343621/115163818-e7ee7580-a0c8-11eb-94a2-fedc861f56ba.png)

After running the file I got:

![26](https://user-images.githubusercontent.com/34343621/115167095-c646bb80-a0d3-11eb-9a9e-22f47d48e6b9.png)


6. Use Jupyter Notebook to create, publish and consume a pipeline.
Pipeline being created. 
![18](https://user-images.githubusercontent.com/34343621/115163853-18ceaa80-a0c9-11eb-8c3a-c5efb94b9e7b.png)

![19](https://user-images.githubusercontent.com/34343621/115163874-3439b580-a0c9-11eb-99ff-622df7409170.png)

This shows Run Details Widget
![20](https://user-images.githubusercontent.com/34343621/115163899-64815400-a0c9-11eb-8e60-b1ca1a7bf4ed.png)

The Run is complete 
![21](https://user-images.githubusercontent.com/34343621/115167106-d199e700-a0d3-11eb-9fb1-60c6422a6f10.png)
![22](https://user-images.githubusercontent.com/34343621/115167111-dced1280-a0d3-11eb-8254-d6d93ec15d6b.png)

Best Model is retervied by this code.
![27](https://user-images.githubusercontent.com/34343621/115167169-1cb3fa00-a0d4-11eb-8a23-4efd7e342fdb.png)


Pulish of the pipeline is done by these lines in notebook. 
![28](https://user-images.githubusercontent.com/34343621/115167190-38b79b80-a0d4-11eb-9964-c4e865c6c837.png)


We can see the pipeline endpoints as well. 
![23](https://user-images.githubusercontent.com/34343621/115167129-ed04f200-a0d3-11eb-9e29-6c33f886801e.png)
![24](https://user-images.githubusercontent.com/34343621/115167137-f1c9a600-a0d3-11eb-8aa9-a119cd5250a5.png)
![25](https://user-images.githubusercontent.com/34343621/115167145-fa21e100-a0d3-11eb-9ada-73bd93f0a322.png)




## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
