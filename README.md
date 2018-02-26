# Azure-Workshop-001

***This is a work in progress - if you have any questions, please contact me.***

Using Azure Traffic Manager, Virtual Machines and CosmosDB to host a globally distributed website.

## What we will be building

We will be using the Azure Cloud Shell to deploy all of the infrastructure.

* Resource Group
* Virtual Machines
* CosmosDB
* More... 

## Getting started

First you will need an Azure Subscription.

If you do not have one, you can sign up for a free trial here; [Azure Free Trial]("https://azure.microsoft.com/en-gb/free/")

### Open the Azure Cloud Shell

To use the Azure Cloud Shell you'll need to create a storage account if you have not done so already.

#### Using the Azure CLI

If you are instead using the Azure CLI to follow this, ensure that you have logged in:

* `az login`
* Type the code received [here](https://login.microsoftonline.com/common/oauth2/deviceauth), and login with your credentials.
* Get your subscription ID: `az account list` 
* Set the correct subscription: `az account set -s <subscriptionid>`
* Confirm you are working in the correct environment: `az account show`

### Creating a Resource Group

We need a resource group to contain all of the resources we will be deploying. This will help us with keeping these logically contained away from other resources, and make cleanup afterwards much simpler!

All you need to create is a name and a location (the resources within are not bound to the location of this resource group)

`az group create -g workshop001 -l westeurope`

### Creating some virtual machines

`az vm create --name vm01 --resource-group workshop001 --location eastus --image UbuntuLTS --size Standard_A1 --generate-ssh-keys`

`az vm create --name vm02 --resource-group workshop001 --location westeurope --image UbuntuLTS --size Standard_A1 --generate-ssh-keys`

`az vm create --name vm03 --resource-group workshop001 --location southeastasia --image UbuntuLTS --size Standard_A1 --generate-ssh-keys`

### Clean up

`az group delete -g workshop001`