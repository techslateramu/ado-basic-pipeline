# Sample Azure Pipelines Configuration

- This repository contains a sample Azure Pipelines configuration file (pipeline-variables.yml) that demonstrates a basic CI/CD pipeline structure with the use of pipeline variables. 
- You can use this as a starting point for setting up your own pipeline.

## Pipeline Overview

- This Azure Pipelines configuration defines a pipeline with two jobs:

### BuildAndTest:

- This job is responsible for running tests for your project.
- It serves as an example of how you can structure your CI jobs.

### DeployToProd:

- This job simulates a deployment to the production environment.
- It includes a condition to only run if the previous job (BuildAndTest) succeeds and if the deployToProduction variable is set to true. 
- This showcases how pipeline variables can control job execution.


## Pipeline Variables
- This configuration file utilizes two pipeline variables:

```
buildConfiguration: This variable specifies the build configuration to be used during the build process. You can customize it based on your project's requirements (e.g., Debug, Release).
```

```
deployToProduction: This boolean variable controls whether the deployment job to the production environment should run. Set it to true to enable production deployments.
```

