# Using a Specific VM Image
In this example, we specify a specific VM image, in this case, 'ubuntu-latest,' as the execution environment for the pipeline:

``` yaml
pool:
  vmImage: 'ubuntu-latest'
```

# Using VM Image Details
You can also specify VM image details such as the ID, publisher, offer, and SKU:

``` yaml
pool:
  vmImage:
    id: 'ubuntu-20.04'
    publisher: 'Canonical'
    offer: 'UbuntuServer'
    sku: '20.04-LTS'
```

# Using a Self-Hosted Agent
If you have a self-hosted agent and want to use it, specify the agent name in the name field:

``` yaml
pool:
  name: MySelfHostedAgent
```

# Using a Hosted Agent Pool
By default, Azure DevOps uses hosted agents. You don't need to specify vmImage or name when using a hosted agent pool:

``` yaml
pool:
  vmImage: 'windows-latest'
```