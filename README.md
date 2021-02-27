# Cloud_assisted_resource_allocation_using_machine_learning
A Resource allocation application using Machine learning technique Assisted by Cloud Computing implemented in Python

## 1 ***Introduction***
An application i've created based on the following paper:
"A Machine Learning Framework for Resource Allocation Assisted by Cloud Computing" which is introducing a framework to do
resource allocation using Machine learning techniques and assist cloud computing for doing the job. for more details refer to the Article. And be aware that this application is a small scale one, probably just a simulator of the real world application.

## 2. ***Data***
#### 2.1 Description
As the system uses Machine learning to allocate the proper resources, we need data. But finding a prepared and clean data
for doing such thing in small scale is not much possible(unless you use Data provided by AWS or Google on massive Data centers).
So i created my own Data. The Data Creator module (Seeder module in /Cloud/storage) uses a predefined template(/Cloud/storage/data/seeder_data_template.csv) to create data. description of attributes, classes, values and ... are in the /Cloud/storage/data/data_description.txt file.

#### 2.2 Process
First the seeder module reads the seeder_data_template.csv file and creates a data based on it in /Cloud/storage/data/dat.csv file.
Attributes, classes and values are manipulatable but needs coding also.

#### 2.3 Execution
To execute the seeder and create the data, run `python3 Cloud/seeder.py`. change the '/' to '\\' in case you are using a non-unix based system.
the command outputs the data.csv file

## 3. Cloud Module

#### 3.1 Description
The Cloud Module is Responsible for Storing Raw data, Preprocessing the Data, Managing the Warehouses, Learn based on the Data
and Create ML model based on it and finally Sending Model To Edges.

#### 3.2 Process
Data is stored in it's storage system and in here, we do the whole learning process in the cloud.py module (in Cloud/Storage/cloud.py, Not a Python Class). the code is fully commented in Docstring format so there is no need for details description but an overview. the Module reads the Data, splits it on 70 percent for training and 30 percent testing, Trains it's model using Decision Tree Classifier Technique, Tests it's model and persists it's model in the storage system.
The Classifier Technique is chosen using Cross validation Technique which showed that Decision Tree can classify the Data with 85 percent Accuracy which is a good number for resource allocation. other techniques like KNN had about 65 percents accuracy on out data

#### 3.3 Execution
The cloud module is executable using `python3 Cloud/cloud.py` command. it outputs a model with joblib format on our storage.
