## Azure ML Ops: Overview of the project
This project aimed at operationalizing a machine learning model. It used a bank marketing dataset related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe a term deposit (variable y) (Copied from https://archive.ics.uci.edu/ml/datasets/bank+marketing). An pipeline was developed which trained an AutoML model usingh the bankmarketing dataset. This pipeline is an automated, reusable and reproducible way to train machine learning models. In addition, an AutoML endpoint was deployed for inference.


## Architectural diagram & Key steps
![Architecture diagram](project_files/screenshots/00_architecture_diagram.PNG)
The top of this image shows the key steps that where taken sequentially for development of the pipeline. The bottom shows the interaction of the different components. The pipeline itself is quite simple since it only consists of an AutoML step, which trains a model with a specific dataset while using a certain compute. No model deployment is included in the pipeline. However it was part of the project, this is why it is shown with a dotted line in the bottom block diagram.

## Possible improvements
The project can be improved in multiple ways:
- Improve prediction accuracy (standard techniques such as more data, feature engineering, training on different models)
- Extending the pipeline with deployment of the best model to an endpoint to be able to train an deploy a working model by consuming a HTTP endpoint
- Making the pipeline more flexible by giving it the option to specify the dataset and target column, this way we create another way to use Azure AutoML apart from the SDK and the Portal.

## [Link to Youtube screencast](https://youtu.be/_OzylQjI5Zw)

## Screenshots, all available in project_files/screenshots directory
Creation of the service principal. This is necessary in order to work with authentication
![image](project_files/screenshots/01_service_principal_created.PNG)
Creation of dataset. Storage of the dataset in Azure makes it easy to re-use the same data for multiple models.
![image](project_files/screenshots/02_dataset_created.PNG)
Completion of AutoML run. An experiment is a group of runs, which itself also can consist of runs. For example this AutoML run consists of multiple sub-runs training different models. As shown, it takes about 30 minutes.
![image](project_files/screenshots/03_automl_run_completed.PNG)
More detail on the completed run, this shows some descriptives of the run, what kind of machine learning problem it is, some detailed of the best model.
![image](project_files/screenshots/04_automl_run_completed_detail.PNG)
Selection of best model. In this case a VotingEnsemble performed best with 0.92 accuracy.
![image](project_files/screenshots/05_best_model.PNG)
Details of best model. This run 47 is a subrun under the main autoML run 1. It also displays metrics like macro and micro AUC
![image](project_files/screenshots/06_best_model_details.PNG)
Logs python script output. This shows the logging output of the model. You can see instances of nginx and guvicorn starting up, application insights being enabled and in the end some succesful 200 OK results for swagger.json.
![image](project_files/screenshots/07_output_logs_py.PNG)
Enabled application insights, on the bottom of the screenshot there is a link to graphically inspect metrics like response time. Application insights can be useful to check if everything is working as planned and spot possible problems.
![image](project_files/screenshots/08_application_insights_enabled.PNG)
Swagger top of page. Swagger shows the documentation for your endpoint. Here we see the /score endpoint, which requires HTTP POST (with the input). It's very useful, because it shows an example of what the endpoint expects to function well.
![image](project_files/screenshots/09_swagger1.PNG)
Swagger bottom of page. The possible outputs (200 OK or an error). On the bottom of the page it shows what the AutoML model expects as input and output. Since the /score endpoint essentially runs the model, it's similar to the top of the page.
![image](project_files/screenshots/09_swagger2.PNG)
Result of API consumption. See also the screencast. In this case, two predications were succesfully made, both resulting in a 'no' response.
![image](project_files/screenshots/11_consume_api_result.PNG)
Benchmarking with Apache top op page. Apache Benchmark can be used to simulate traffic to your endpoint, giving insights in how the model performs in terms of response. Here we see the tool making several request, all ending with 200 OK.
![image](project_files/screenshots/12_apache_benchmark.PNG)
Benchmarking with Apache bottom of page. The benchmark made 10 requests. Especially the bottom table is interesting, since it shows the median response time (243), but also some worse performances, essentially creating a distribution of the response times.
![image](project_files/screenshots/13_apache_benchmark_2.PNG)
Creation of pipeline. A pipeline is a number of steps strung together. It's very useful for automation, structure and reproducibility. In this case the pipeline consisted of training an AutoML model on the bankmarketing dataset.
![image](project_files/screenshots/14_pipeline_created.PNG)
Active pipeline endpoint. The pipeline endpoint makes it possible to active a pipeline by consuming it from HTTP. Note that in this screenshot the endpoint had not yet been consumed.
![image](project_files/screenshots/15_pipeline_endpoint_active.PNG)
Detail of active pipeline endpoint. The steps are shown, as well as the REST Endpoint to use. The status is active, meaning it can be consumed.
![image](project_files/screenshots/16_pipeline_endpoint_detail.PNG)
Bankmarketing dataset used as input for AutoML step
![image](project_files/screenshots/17_bankmarketing_dataset_used.PNG)
Pipeline run, this basically does the same thing as the next screenshot, but this was the initial pipeline run, not from the endpoint.
![image](project_files/screenshots/18_pipeline_run.PNG)
Pipeline run, this basically does the same thing as the previous, but this time, it was automatically initiated by consuming the endpoint, as shown on the right (run type=HTTP).
![image](project_files\screenshots\21_pipeline_endpoint_run_completed_detail.PNG)
Here you also see the endpoint run completed succesfully
![image](project_files\screenshots\20_pipeline_endpoint_run_completed.PNG)
Run_detail output from jupyter, we see the steps graphically depicted along with some timing information.
![image](project_files/screenshots/19_jupyter_run_detail.PNG)