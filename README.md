# ClaimsVariables
Utilizing ADO pipeline template for setting variables with respect to Blue/Green deployment orchestration changes, Pushing cosmos log for Blue/Green deployment, Refactored apijobs  pipelines for multiple cluster pods deployment

## Pipeline Requirements

The setVariable pipeline requires the following parameters to be defined:
Paramaters:


| Name  | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| appDeploymentTarget | string | | | Required | |
| key | string | | | Required | |
| enableClaimsVariables | boolean | 'true' | 'true'/'false' | Required | |


These parameters provide multiple use case options for the setvariables templates pipeline, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

### Direct use of a template

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/terraform.validate.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'



  steps:  
   # passing the parameters
  - template: templates/claimsVariables.yml@Template
      parameters:
        appDeploymentTarget: ${{parameters.appDeploymentTarget}}
        key: ${{parameters.key}}


Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

  ```
