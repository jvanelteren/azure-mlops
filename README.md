## Azure ML Ops: Overview of the project
This project aimed at operationalizing a machine learning model. It used a bank marketing dataset where the object The data is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe a term deposit (variable y) (Copied from https://archive.ics.uci.edu/ml/datasets/bank+marketing). An AutoML pipeline was developed which used the bankmarketing dataset and predicted variable y. This pipeline is an automated, reusable and reproducible way to train machine learning models. 


## Architectural diagram & Key steps
![Architecture diagram](project_files/screenshots/00_architecture_diagram.PNG)
The top of this image shows the key steps that where taken sequentially. The bottom shows the interaction of the different components. The pipeline itself is quite simple since it only consists of an AutoML step, which trains a model with a specific dataset while using a certain compute. No model deployment is included in the pipeline.

## Possible improvements
The project can be improved in multiple ways:
- improve prediction accuracy (standard techniques such as more data, feature engineering, different models)
- Extending the pipeline with deployment of the best model to an HTTP endpoint to be able to train a working model by consuming a HTTP endpoint
- Making the pipeline more flexible by giving it the option to specify the dataset and target column, this way we create another way to use Azure apart from the SDK and the Portal.

## [Link to Youtube screencast](https://youtu.be/_OzylQjI5Zw)

## Screenshots, all available in project_files/screenshots directory
Creation of the service principal
![image](project_files\screenshots\01_service_principal_created.PNG)
Creation of dataset
![image](project_files\screenshots\02_dataset_created.PNG)
Completion of AutoML run
![image](project_files\screenshots\03_automl_run_completed.PNG)
Selection of best model
![image](project_files\screenshots\05_best_model.PNG)
Details of best model
![image](project_files\screenshots\06_best_model_details.PNG)
Logs python script output
![image](project_files\screenshots\07_output_logs_py.PNG)
Enabled application insights
![image](project_files\screenshots\08_application_insights_enabled.PNG)
Swagger top of page
![image](project_files\screenshots\09_swagger1.PNG)
Swagger bottom of page
![image](project_files\screenshots\09_swagger2.PNG)
Result of API consumption
![image](project_files\screenshots\11_consume_api_result.PNG)
Benchmarking with Apache top op page
![image](project_files\screenshots\12_apache_benchmark.PNG)
Benchmarking with Apache bottom of page
![image](project_files\screenshots\13_apache_benchmark_2.PNG)
Creation of pipeline
![image](project_files\screenshots\14_pipeline_created.PNG)
Active pipeline endpoint
![image](project_files\screenshots\15_pipeline_endpoint_active.PNG)
Detail of active pipeline endpoint
![image](project_files\screenshots\16_pipeline_endpoint_detail.PNG)
Bankmarketing dataset used as input for AutoML step
![image](project_files\screenshots\17_bankmarketing_dataset_used.PNG)
Pipeline run
![image](project_files\screenshots\18_pipeline_run.PNG)
Run_detail output from jupyter
![image](project_files\screenshots\19_jupyter_run_detail.PNG)