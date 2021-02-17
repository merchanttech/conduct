# Continuous integration

A guide for development continuous integration workflow within TheMTMAgency.

## Tools we use for continuous integration:

- [Github](https://github.com)
- PHP
  - [DeployHQ](https://deployhq.com)
  - [DigitalOcean](https://digitalocean.com)
- WordPress
  - [WPengine](https://wpengine.com)
- .NET
  - [Azure DevOps](https://azure.microsoft.com/en-gb/services/devops/)
  - [Microsoft Azure](https://portal.azure.com)

## Workflow

As stated in the [git](../git) protocol you should always work in feature branches and never commit directly to master.

**General**

- Once you work is done, push the feature branch to the GitHub repo and create a pull request.
- After the pull request has been approved or work has been implemented the branch gets merged into master.

**PHP**

- For the staging environment (UAT), DeployHQ will automatically pick up the code changes and will deploy to UAT server.
- Once the tests pass on the UAT, deployment to the LIVE environment has to be done manually from DeployHQ.

**WordPress**

- For the dev environment, WPengine will automatically pick up the code changes and will deploy to the cloud server.

**.NET**

- For the QA environment, Azure DevOps Pipelines will automatically pick up the code changes and will deploy to the server.
- Once the tests pass on the QA, deployment to the UAT environment has to be done manually from Azure DevOps.
