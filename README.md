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
