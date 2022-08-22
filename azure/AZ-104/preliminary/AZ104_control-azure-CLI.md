For tasks that need to be repeated daily, or even hourly, using the command line and a set of tested commands or scripts can help get your work done more quickly and avoid errors.

# What is the Azure CLI?

The Azure CLI is a command-line program to connect to Azure and execute administrative commands on Azure resources.

It runs on Linux, macOS, and Windows, and allows administrators and developers to execute their commands through a terminal or command-line prompt (or script!) instead of a web browser. 

```
az vm restart -g MyResourceGrou -n MyVm
```

Azure CLI provides cross-platform command-line tools for managing Azure resources, and you can easily install it locally on Linux, Mac, or Windows computers.

The Azure CLI can be used from a browser through the Azure Cloud Shell.

Can be used:
- Interactively
- Using Scripts

## How to install the Azure CLI

- Linux: apt-get on Ubuntu, yum on Red Hat, and zypper on OpenSUSE
- Mac: Homebrew
- The Azure CLI is available in the Microsoft repository or through MSI

## Scripts: Azure CLI 

For the scripts:

```azure
variable="value"
variable=integer
```

```powershell
$variable="value"
$variable=integer
```

Azure CLI must be installed before you can use it to manage Azure resources from a local computer.


## What Azure Resources can be managed using the Azure CLI?

You can work with resource groups, storage, virtual machines, Azure Active Directory (Azure AD), containers, machine learning, and so on.

Commands in the CLI are structured in groups and subgroups:

- Each group represents a service provided by Azure. 
- Subgroups divide commands for these services into logical groupings. 

```
az find <command>
```

Also you can use the ```--help``` argument:
```
az storage blog --help
```

## How to create an Azure Resource
Three steps:
1. Connect to your Azure subscription
2. Create the resource
3. Verify the creation was successfull.

### 1. Connect
```
az login
```

### 2. Create
Often you need to create a **new resource group** before you create a new Azure service:

```
az group create --name <name> --location <location>
```

- Name must be unique within your subscription
- Location determines where the metadata for your RG will be stored. 

### 3. Verify 

For many Azure Resources the CLI provides a ```list``` subcomamand to view resource details.

```
az group list
```

To get more concise view:

```
az group list --output table
```

# Lab

```sh
export RESOURCE_GROUP=learn-790bc9ad-120e-4f77-8709-811008090425
export AZURE_REGION=centralus
export AZURE_APP_PLAN=popupappplan-$RANDOM
export AZURE_WEB_APP=popupwebapp-$RANDOM
```


Filtering results:

```
az group list --query "[?name == '$RESOURCE_GROUP']"
```

## Steps to create a service plan 

The name of the app and plan must be unique in all of Azure. 

```
az appservice plan create --name $AZURE_APP_PLAN --resource-group $RESOURCE_GROUP --location $AZURE_REGION --sku FREE 
```

```
az appservice plan list --output table
```

## Steps to create a web app

```
az webapp create --name $AZURE_WEB_APP --resource-group $RESOURCE_GROUP --plan $AZURE_APP_PLAN
```

To veryfy:

```
az webapp list --output table
```

And check the available web site:
```shell
curl $AZURE_WEB_APP.azurewebsites.net
```

### Steps to deploy code from GitHub

```
az webapp deployment source config --name $AZURE_WEB_APP --resource-group $RESOURCE_GROUP --repo-url "https://github.com/Azure-Samples/php-docs-hello-world" --branch master --manual-integration
```

