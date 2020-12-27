# Machine-Learning
d

from azureml.core import ScriptRunConfig
compute_target = ws.compute_targets['<my-cluster-name>']
src = ScriptRunConfig(source_directory='.',
                      script='train_iris.py',
                      arguments=['--kernel', 'linear', '--penalty', 1.0],
                      compute_target=compute_target,
                      environment=sklearn_env)
  
  
  from azureml.core import Environment
sklearn_env = Environment.get(workspace=ws, name='AzureML-Tutorial')


%%writefile conda_dependencies.yml
dependencies:
- python=3.6.2
- scikit-learn
- pip:
  - azureml-defaults
  
  
  
  rom azureml.core import Environment
from azureml.core import ScriptRunConfig
sklearn_env = Environment.from_conda_specification(name = 'sklearn-env', file_path = './envs/conda_dependencies.yml')
src = ScriptRunConfig(source_directory=script_folder,
                      script='train.py',
                      compute_target=compute_target,
                      environment=sklearn_env)


best_run_metrics=automl_run.get_metrics()
for primary_metric in best_run_metrics:
    metric=best_run_metrics[primary_metric]
    print(primary_metric,metric)


best_automl_run,best_automl_model=automl_run.get_output()
joblib.dump(value=best_automl_model,filename='automl_model.joblib')
