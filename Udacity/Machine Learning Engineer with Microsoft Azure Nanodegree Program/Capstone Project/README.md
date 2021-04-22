

# Heart Failure Prediction

Cardiovascular diseases (CVDs) are the number 1 cause of death globally, taking an estimated 17.9 million lives each year, which accounts for 31% of all deaths worlwide.
Heart failure is a common event caused by CVDs and this dataset contains 12 features that can be used to predict mortality by heart failure.

Most cardiovascular diseases can be prevented by addressing behavioural risk factors such as tobacco use, unhealthy diet and obesity, physical inactivity and harmful use of alcohol using population-wide strategies.

People with cardiovascular disease or who are at high cardiovascular risk (due to the presence of one or more risk factors such as hypertension, diabetes, hyperlipidaemia or already established disease) need early detection and management wherein a machine learning model can be of great help.


## Project Set Up and Installation
As I did all of the work in dacity Lab there was no need of any special installations, Udacity and Microsoft took care of it very neatly. All I had to do was lauch ML Studio. 

## Dataset

### Overview
The dataset is taken from Kaggle, a place for open source datasets. There are 12 coloums which are: age, anaemia, creatinine, diabetes, ejection_fraction, high_blood_pressure, platelets, serum_creatinine, serum_sodium, sex, smoking and time. 13th coloum is the target which is DEATH_EVENT. 

### Task
The task is to build model with AutoML as well as HyperDrive, compare both of them and the one which is better is to be depolyed. As target coloum is DEATH_EVENT which has entires in binary result will be binary as well. The 0 zero entry indicates that death will not occur while 1 is opposite of that. 

### Access
To access the dataset URL method is used, although creating dataset could also have been used. 

## Automated ML
As the ned results were 0 and 1 only and that too only balanced dataset, classification with AutoML was best option. Along with it the other parameters which were given were:
n_cross_validations = 8
It is used to determine how many cross-validations to perform when user validation data is not specified. 
primary_metric = accuracy
It is used to find the best algorithm in AutoML with respect to accuracy.
enable_early_stopping = True
This prevents the model to not fall into the loop if the score of primary metric which in my case was accuracy does not seem to improve. 
experiment_timeout_minutes = 20
It is the number of time iterations can take before ending, we set the value to 20 minutes here as our dataset is not that large. 
max_concurrent_iterations = 15
A number of iterations that can run at the same time making AutoML consume less time and improve predictions.

### Results
The best model obtained from the AutoML run was given by VotingEnsemble with an accuracy of about 88%. 
To increase this accuracy, experiments can be run for a longer time, and changing in primary metric can be effective as well.

AutoML Run
![1](https://user-images.githubusercontent.com/34343621/115318245-02911f00-a19b-11eb-83b7-3bddce68bea7.png)

RunDetails
![2](https://user-images.githubusercontent.com/34343621/115318247-03c24c00-a19b-11eb-8bd1-6a8f363e00d0.png)

Best AutoML Model
![3](https://user-images.githubusercontent.com/34343621/115318248-045ae280-a19b-11eb-88df-def90e38f842.png)

![4](https://user-images.githubusercontent.com/34343621/115318249-04f37900-a19b-11eb-88cf-df660affa4ed.png)


## Hyperparameter Tuning
As classification was used in AutoML for binary entries, the algorithm chosen with Hyperparameter Tuning is Logistic regression. 
Accuracy was kept the primary metric same as AutoML to compare them so that one can be deployed. 
max_total_runs = 30
max_cocurrent_runs = 5
These numbers were kept to increase efficiency. Also, an early termination policy was used. 

### Results
The Hyperdrive run came quite close to AutoMl with an accuracy of 86.6%, surely increasing the number of runs would have narrowed the gap even further. Also, including other hyperparameters can change the model quite a lot and make it equal to AutoML which tunning. 

HyperDrive Run
![5](https://user-images.githubusercontent.com/34343621/115319218-ee4e2180-a19c-11eb-8c88-435dfdbf5c6b.png)

![6](https://user-images.githubusercontent.com/34343621/115319220-ef7f4e80-a19c-11eb-868c-760503b5b43b.png)

![7](https://user-images.githubusercontent.com/34343621/115319221-f017e500-a19c-11eb-814e-fe53078be6d3.png)

Best Model 
![8](https://user-images.githubusercontent.com/34343621/115319224-f017e500-a19c-11eb-8f2c-e216dba83a65.png)


## Model Deployment
There was not much difference in AutoML and HyperDrive run but since AutoML was a bit higher I went with the deployment of AutoML. The model is deployed using Azure Container Instance(ACI) web services which had application insights and gave a URI to visualize it. 
To test it, two data entries were given, and the answer was verified from the Kaggle notebooks. 

![90](https://user-images.githubusercontent.com/34343621/115319531-a5e33380-a19d-11eb-91f7-bd4f825b29a4.png)

![94](https://user-images.githubusercontent.com/34343621/115753166-8411c880-a3b8-11eb-9ac6-9d3f39dcece7.png)

![91](https://user-images.githubusercontent.com/34343621/115319537-a7146080-a19d-11eb-86df-ac338631ddaa.png)

![93](https://user-images.githubusercontent.com/34343621/115319540-a7acf700-a19d-11eb-837c-ae446fce365a.png)

## Screen Recording
Link to recording - https://youtu.be/N7GIu3pQkno


