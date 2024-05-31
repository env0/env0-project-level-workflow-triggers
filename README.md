# env0-workflow-triggers-plugin
This Plugin will allow you to run deployment triggers as part of a custom flow, extending the ability to define triggers at environment creations, at the project level, or when destroying an environment.

## Inputs

The workflow triggers plugin accepts the following inputs:

* `downstream-environment` (required) - the environment ID of the environment that should be triggerred 
* `env0-api-key` (required) - The API key for the env0 organization 
* `env0-api-secret` (required) - The API secret for the env0 organization 

## Example Usage



In this example we will trigger a deployment of an environment at following a successful completion or successful destory of an environment, where the required inputs are provided using environment variables:

```yaml
version: 2
deploy:
  onSuccess:
    - name: Trigger Envrionment on Deploy
      use: https://github.com/env0/env0-workflow-triggers-plugin
      inputs:
        downstream-environment: $TRIGGER_ENVIRONMENT
        env0-api-key: $ENV0_API_KEY
        env0-api-secret: $ENV0_API_SECRET

destroy:
  onSuccess:
    - name: Trigger Envrionment on Destroy
      use: https://github.com/env0/env0-workflow-triggers-plugin
      inputs:
        downstream-environment: $TRIGGER_ENVIRONMENT
        env0-api-key: $ENV0_API_KEY
        env0-api-secret: $ENV0_API_SECRET

```
