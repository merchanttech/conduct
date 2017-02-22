Continuous integration
======================

A guide for development continuous integration workflow within TheMTMAgency.

Tools we use for continuous integration:
----------------------------------------

* [Github](https://github.com)
* PHP
  * [DeployHQ](https://deployhq.com)
  * [DigitalOcean](https://digitalocean.com)
* .NET
  * TeamCity
  * Octopus Deploy
  * [Microsoft Azure](https://portal.azure.com)

Workflow
--------

As stated in the [git](../git) protocol you should always work in feature branches and never commit directly to master.

**General**

* Once you work is done push the feature branch onto the Github repo and create a pull request
* After the pull request has been approved or work has been implemented the branch gets merged into master.

**PHP**

* For the staging environment (UAT), DeployHQ will automatically pick up the code changes and will deploy to UAT server.
* Once the tests pass on the UAT, deployment to the LIVE environment has to be done manually from DeployHQ.

**.NET**

* Coming soon...
