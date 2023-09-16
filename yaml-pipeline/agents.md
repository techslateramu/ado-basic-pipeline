# Triggering Pipelines in Azure DevOps

Azure DevOps pipelines support various trigger types to automate your CI/CD workflows. Below are some examples of trigger configurations in Azure DevOps YAML pipelines.

- Push Trigger
- Pull Request Trigger
- Scheduled Trigger
- Webhook Trigger
- Manual Trigger
- Tag Trigger
- Dependency Trigger
- Pipeline Resource Trigger

## Push Trigger
Triggered when code is pushed to specific branches.

```yaml
trigger:
  branches:
    include:
      - main
      - feature/first-branch
```
## Push Trigger
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
## Scheduled Trigger
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

## Webhook Trigger
Triggered by an external webhook event.

``` yaml
pr: none  # Disable PR triggers
trigger:
  branches:
    include:
      - '*'
```


##  Manual Trigger
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

## Tag Trigger:
Triggered when a new tag is pushed.

``` yaml
trigger:
  tags:
    include:
      - v1.*
```

##  Dependency Trigger
Triggered after a specific job or pipeline is completed successfully.

``` yaml
dependencies:
  - dependencyJob  # Name of the job to depend on
```

##  Pipeline Resource Trigger
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
