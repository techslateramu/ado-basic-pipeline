
# <span style="color: blue;">YAML Pipeline-Basic</span>
- This is the basic yaml pipeline, which contains triggers, pool, stages, jobs and tasks with examples


## Triggering Pipelines in Azure DevOps

Azure DevOps pipelines support various trigger types to automate your CI/CD workflows. Below are some examples of trigger configurations in Azure DevOps YAML pipelines.

- Push Trigger
- Pull Request Trigger
- Scheduled Trigger
- Webhook Trigger
- Manual Trigger
- Tag Trigger
- Dependency Trigger
- Pipeline Resource Trigger

### Push Trigger
Triggered when code is pushed to specific branches.

```yaml
trigger:
  branches:
    include:
      - main
      - feature/first-branch
```
### Push Trigger
Triggered when code is pushed to specific branches.

```yaml
trigger:
  branches:
    exclude:
      - '*'
  paths:
    include:
      - '*'
```
### Scheduled Trigger
Triggered at specific time intervals or schedules.

```yaml
schedules:
  - cron: "0 0 * * *"
    displayName: Daily build trigger
```
### CRON explained

CRON is a time-based job scheduling system used in Unix-like operating systems, including Linux. It allows you to schedule tasks or commands to run automatically at specific times or intervals. The term "CRON" itself is derived from the Greek word "chronos," which means time.

```
* * * * * command-to-be-executed
| | | | |
| | | | +----- Day of the week (0 - 6) (Sunday=0 or 7)
| | | +------- Month (1 - 12)
| | +--------- Day of the month (1 - 31)
| +----------- Hour (0 - 23)
+------------- Minute (0 - 59)
```

```
* * * * * command: This job runs every minute of every hour, every day.
0 2 * * * command: This job runs at 2:00 AM every day.
0 0 * * 1 command: This job runs at midnight on Mondays (Day of the week 1).
0 0 1 * * command: This job runs at midnight on the 1st day of every month.
```

### Webhook Trigger
Triggered by an external webhook event.

``` yaml
pr: none  # Disable PR triggers
trigger:
  branches:
    include:
      - '*'
```


###  Manual Trigger
Requires manual intervention to start the pipeline.

``` yaml
pr: none  # Disable PR triggers
trigger:
  branches:
    include:
      - main
  paths:
    include:
      - '*'
``` 

### Tag Trigger:
Triggered when a new tag is pushed.

``` yaml
trigger:
  tags:
    include:
      - v1.*
```

###  Dependency Trigger
Triggered after a specific job or pipeline is completed successfully.

``` yaml
dependencies:
  - dependencyJob  # Name of the job to depend on
```

###  Pipeline Resource Trigger
Triggered when a resource, such as an artifact, is updated.

``` yaml
resources:
  pipelines:
    - pipeline: pipelineResource
      source: PipelineName
      trigger:
        branches:
          include:
            - main
```


## Running Agents


### Using a Specific VM Image
In this example, we specify a specific VM image, in this case, 'ubuntu-latest,' as the execution environment for the pipeline:

``` yaml
pool:
  vmImage: 'ubuntu-latest'
```

### Using VM Image Details
You can also specify VM image details such as the ID, publisher, offer, and SKU:

``` yaml
pool:
  vmImage:
    id: 'ubuntu-20.04'
    publisher: 'Canonical'
    offer: 'UbuntuServer'
    sku: '20.04-LTS'
```

### Using a Self-Hosted Agent
If you have a self-hosted agent and want to use it, specify the agent name in the name field:

``` yaml
pool:
  name: MySelfHostedAgent
```

### Using a Hosted Agent Pool
By default, Azure DevOps uses hosted agents. You don't need to specify vmImage or name when using a hosted agent pool:

``` yaml
pool:
  vmImage: 'windows-latest'
```


# <span style="color: blue;">YAML Pipeline-Variables</span>
- This is the basic yaml pipeline, which explains how to use pipeline variables

## variables with in the code  

``` yaml
variables:
  buildConfiguration: 'Release'
  deployToProduction: true  # Define a single variable for deployment
```

## variables consider as pipeline variabels
- set the variable in pipeline and use it in code


# <span style="color: blue;">YAML Pipeline-Group-Variables</span>
- Add Group Variables in Library section
- Attach them to Stages or to the pipeline 

``` yaml
variables:
  - group: common
```
 the variables inside common group can be accessed through out the pipelines

``` yaml
- stage: Prod
  variables:
  - group: env-prod
  jobs:
  - job: Prod1
    displayName: 'Prod Job 1'
    steps:
    - script: echo 'Running Prod Job 1'
```
 the variables inside env-prod group can be accessed through only in PROD stage


# <span style="color: blue;">YAML Pipeline-Approval</span>
- Create an Environment called 'Prod-Approvers' and approvers into it

``` yaml
stages:
- stage: Prod
  jobs:
  - deployment: DeployToProd
    displayName: 'Deploy to Prod'
    environment: Prod-Approvers
    strategy:
      runOnce:
        deploy:
          steps:
          - script: echo 'Running Prod Job 1'
```