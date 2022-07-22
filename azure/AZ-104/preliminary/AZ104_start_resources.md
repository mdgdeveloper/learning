# Azure Portal

The Azure portal lets you build, manage, and monitor everything from simple web apps to complex cloud applications in a single, unified console.

## Azure Portal features

- Search resources, services, and docs.
- Manage resources.
- Create customized dashboards and favorites.
- Access the Cloud Shell.
- Receive notifications.
- Links to the Azure Docs. 


# Azure Cloud Shell

Interactive, browser-accessible shell for managing Azure resources. 

It provides the flexibility of choosing the shell experience that best suits the way you work. 

💡 Linux users can opt for a Bash experience, while Windows users can opt for PowerShell.

## Azure Cloud Shell features 

- Is temporary and requires a new or existing Azure Files share to be mounted.
- Offers an integrated graphical text editor based on the open-source Monaco Editor.
- Authenticates automatically for instant access to your resources.
- Runs on a temporary host provided on a per-session, per-user basis.
- Times out after 20 minutes without interactive activity.
- 🟡 Requires a resource group, storage account, and Azure File share. 
- Uses the same Azure file share for both Bash and PowerShell
- Is assigned to one machine per user account. 
- Persists $HOME using a 5-GB image held in your file share.
- Permissions are set as a regular Linux user in Bash. 

# Azure PowerShell

Azure PowerShell is a module that you add to Windows PowerShell or PowerShell Core to enable you to connect to your Azure subscription and manage resources.

Azure PowerShell requires PowerShell to function. PowerShell provides services such as the shell window and command parsing. Azure PowerShell adds the Azure-specific commands.

Azure PowerShell is also available two ways: 
- Inside a browser via the **Azure Cloud Shell**.
- With a **local installation** on Linux, macOS, or the Windows operating system.

Two modes: 
- interactive mode: manually issue one command at a time
- scripting mode: execute a script that consists of multiple commands.

## Az Module

Azure PowerShell module containing cmdlets to work with Azure features.

Features:

- Resources groups
- Storage
- VMs
- Azure AD
- Containers
- Machine learning.

# Azure CLI 
Azure CLI is a command-line program to connect to Azure and execute administrative commands on Azure resources.

Runs on Linux, macOS, and Windows, and allows administrators and developers to execute their commands through a terminal, command-line prompt, or script instead of a web browser. 

Example
```sh
az vm restart -g MyResourceGroup -n MyVm
```

Provides cross-platform command-line tools for managing Azure resources.

Can be used:

- Local
- Azure Cloud Shell

Two modes: 
- Interactive mode: manually issue one command at a time
- Scripting mode: execute a script that consists of multiple commands.

Features:

- Resources groups
- Storage
- VMs
- Azure AD
- Containers
- Machine learning.


Commands in the CLI are structured in:
- Groups: represents a service provided by Azure. (e.g. Storage)
- Subgroups: divide commands for these services into logical groupings (e.g. account, blob, share, queue)

Find a particular command: ```az find```

Help: ```--help```

