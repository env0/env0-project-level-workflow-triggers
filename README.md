# env0-project-level-workflow-triggers
This Plugin will allow you to run deployment triggers as part of a custom flow, extending the ability to define triggers at environment creations, at the project level, or when destroying an environment.

## Inputs

The trivy plugin accepts the following inputs:

* `downstream-environment` (required) - the environment ID of the environment that should be triggerred 


## Example Usage



In this example we will trigger a deployment of an environment at following a successful completion or successful destory of an environment, the required `downstream-environment` inout is provided as part of an environment variable named `TRIGGER_ENVIRONMENT`:

```yaml
version: 2
deploy:
  onSuccess:
    - name: Trigger Envrionment on Deploy
      use: https://github.com/env0/env0-project-level-workflow-triggers@correct-plugin
      inputs:
        downstream-environment: $TRIGGER_ENVIRONMENT

destroy:
  onSuccess:
    - name: Trigger Envrionment on Destroy
      use: https://github.com/env0/env0-project-level-workflow-triggers@correct-plugin
      inputs:
        downstream-environment: $TRIGGER_ENVIRONMENT

```
