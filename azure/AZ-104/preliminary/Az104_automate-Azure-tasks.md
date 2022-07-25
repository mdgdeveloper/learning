# Tools available

Azure provides three administration tools:
- The Azure portal
- The Azure CLI
- Azure PowerShell

> All three are cross-platform 

## Azure Portal

Website that lets you create, configure, and alter the resources in your Azure subscription. 

Uses a GUI. 

Provides wizards and tooltips. 

The portal does NOT provide any way to automate repetitive tasks. 

## Azure CLI

The Azure CLI is a cross-platform command-line program to connect to Azure and execute administrative commands on Azure resources 

```bash
az vm create \
  --resource-group CrmTestingResourceGroup \
  --name CrmUnitTests \
  --image UbuntuLTS
  ...

```

Azure CLI is available in two ways:

* Inside a browser => Azure Cloud Shell
* Local install on Linux, Mac or Windows. 

You can use interactively OR use **scripts** to automate tasks. 

## Azure PowerShell

Azure PowerShell is a modlue you add to PowerShell to let you connect to your Azure subscriptions. 

Requires PowerShell to work. 

Example:
```powershell
New-AzVm `
    -ResourceGroupName "CrmTestingResourceGroup" `
    -Name "CrmUnitTests" `
    -Image "UbuntuLTS"
    ...
```

Azure PowerShell is available in two ways:

* Inside a browser => Azure Cloud Shell
* Local install on Linux, Mac or Windows. 

You can use interactively OR use **scripts** to automate tasks. 

## How to choose

Considerations:

- **Automation** 
- **Learning curve**
- **Team skillset**

# Install PowerShell 

- The base **PowerShell** product This comes in two variants: Windows PowerShell and PowerShell 7.x, which can be installed on Windows, macOS, and Linux.
- The **Azure Az PowerShell module** This extra module must be installed to add the Azure-specific commands to PowerShell.

## How to install PowerShell

Both Linux and macOS: package manager.

### Linux

| Distribution | Package manager| 
| - | - | 
| Ubuntu, Debian | apt-get |
| Red Hat, CentOS | yum |
| OpenSUSE | zypper | 
| Fedora | dnf | 


## Mac

Homebrew


# Create Azure Resource using scripts in Azure PowerShell

## Cmdlets

A PowerShell command is called a cmdlet (pronounced "command-let"). A cmdlet is a command that manipulates a single feature. The term cmdlet is intended to imply "small command". By convention, cmdlet authors are encouraged to keep cmdlets simple and single-purpose.

## PowerShell module

Cmdlets are shipped in modules. A PowerShell Module is a DLL that includes the code to process each available cmdlet.

You can get a list of loaded modules using the ```Get-Module```.

## Az PowerShell module

Az is the formal name for the Azure PowerShell module, which contains cmdlets to work with Azure features.

You can work with resource groups, storage, virtual machines, Azure Active Directory, containers, machine learning, and so on. 

> This module is an **open-source** component available on GitHub. 

## Install Az PowerShell module

```
Install-Module -Name Az -Scope CurrentUser -Repository PSGallery
```

You can check the execution policy by running the cmdlet Get-ExecutionPolicy. If it returns "Restricted", then do the following:

Use the SetExecutionPolicy cmdlet to change the policy to "RemoteSigned":
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

## Update a PowerShell module

```powershell
Update-module -Name Az
```

### ✨ Example: Create resource group with Azure PowerShell

There are four steps you need to perform:

1. Import the Azure cmdlets.
2. Connect to your Azure subscription.
3. Create the resource group.
4. Verify that creation was successful.

#### 1. Import the Azure cmdlets.

Beginning with PowerShell 3.0, modules are loaded automatically when you use a cmdlet within the module. It's no longer necessary to manually import PowerShell modules unless you've changed the default module autoloading settings.

#### 2. Connect to your Azure subscription.

The Connect-AzAccount cmdlet prompts for your Azure credentials, then connects to your Azure subscription.

```powershell
Connect-AzAccount
```

You can configure Azure PowerShell to execute commands against a particular subscription.

You can only be in one subscription at a time. Use the ```Get-AzContext``` cmdlet to determine which subscription is active.

To change the subscription you are using:

1. Get a list of all subscription names in your account with the ```Get-AzSubscription``` command.
2. Change the subscription by passing the name of the one to select.

```powershell
Set-AzContext -Subscription '00000000-0000-0000-0000-000000000000'
```

> If you need to look up the Subscription ID, open Azure and select Subscriptions on the home page.

#### 3A. Get a list of all resource groups 

You can retreive a list of **all Resource Groups** in the active subscription: ```Get-AzResourceGroup```

More concise view:

```powershell
Get-AzResourceGroup | Format-Table
```

#### 3B. Create a Resource Group 

A resource group is often one of the first things you'll create when starting a new application.

You can create resource groups by using the ```New-AzResourceGroup``` cmdlet. You must specify a name and location. 

- Name must be **unique**. 
- Location determines where the metadata will be stored. 

```
New-AzResourceGroup -Name <name> -Location <location>
```

#### 4. Verify the resources

Basic ```Get-AzResource``` to list the new created resource groups:

```powershell
Get-AzResource
```

Or format it: 

```powershell
Get-AzResource | Format-Table
```

Or filter it: 

```powershell
Get-AzResource -ResourceGroupName ExerciseResources
```

### Create an Azure Virtual Machine

Azure PowerShell provides the ```New-AzVm``` cmdlet to create a virtual machine.

The parameters to define: 
* ResourceGroupName: The resource group into which the new VM will be placed.
* Name: The name of the VM in Azure
* Location: Geographic location where the VM will be provisoned.
* Credential: Object with Username and Password. We will use ```Get-Credential``` cmdlet. 
* Image: The OS image to use for the VM. 


```powershell
New-AzVm
    -ResourceGroupName <resource group name>
    -Name <machine name>
    -Credential <credentials object>
    -Location <location>
    -Image <image name>
```

Alternatively, you can use other cmdlets to configure the virtual machine, such as ```Set-AzVMOperatingSystem```, ```Set-AzVMSourceImage```, ```Add-AzVMNetworkInterface```, and ```Set-AzVMOSDisk```.

Example with ```Get-Credential```:

```powershell
New-AzVM -Name MyVm -ResourceGroupName ExerciseResources -Credential (Get-Credential) ...
```

Other cmdlets:

| Command | Description |
| - | - |
| Remove-AzVM | Deletes an Azure VM |
| Start-AzVM | Start a stopped VM | 
| Stop-AzVM | Stop a runnung VM | 
| Restart-AzVM | Restart a VM |
| Update-AzVM | Updates the configuration for a VM | 


#### Example: Getting information from a VM

List the VM in your subscription: ```Get-AzVM -Status```


Assign it to a PS variable:
```powershell
$vm = Get-AzVM -Name MyVM -ResourceGroupName ExerciseResources
```

Use it in a script:
```powershell
$ResourceGroupName = "ExerciseResources"
$vm = Get-AzVM  -Name MyVM -ResourceGroupName $ResourceGroupName
$vm.HardwareProfile.vmSize = "Standard_DS3_v2"

Update-AzVM -ResourceGroupName $ResourceGroupName  -VM $vm
```

> The interactive mode in PowerShell is appropriate for one-off tasks.

Properties: 

```powershell
$vm.HardwareProfile
```

Info about one of the disks:

```powershell
$vm.StorageProfile.OsDisk
```

You can also pass the VM object to other cmdlets:

```powershell
$vm | Get-AzVMsize
```

Get the Public IP address:

```powershell
Get-AzPublicIpAddress -ResourceGroupName <resource group name> -Name <name of the VM>
```

### Delete a VM 

1. Shut it down:
```powershell
Stop-AzVM -Name $vm.Name -ResourceGroupName $vm.ResourceGroupName
```

2. Delete the VM:
```powershell
Remove-AzVM -Name $vm.Name -ResourceGroupName $vm.ResourceGroupName
```

3. List all the resources in your resource group
```powershell
Get-AzResource -ResourceGroupName $vm.ResourceGroupName | Format-Table
```

**Important:** The ```Remove-AzVM``` command just deletes the VM. It doesn't clean up any of the other resources. 

To delete the rest of the resources associated to the VM:

1. Delete the network interface
```powershell
$vm | Remove-AzNEtworkInterface -Force
```

2. Delete the manged OS disks and storage account:
```powershell
Get-AzDisk -ResourceGroupName $vm.ResourceGroupName -DiskName $vm.StorageProfile.OsDisk.Name | Remove-AzDisk -Force
```

3. Delete the Virtual Network:
```powershell
Get-AzVirtualNetwork -ResourceGroupName $vm.ResourceGroupName | Remove-AzVirtualNetwork -Force
```

4. Delete Network Security Group
```powershell
Get-AzNetworkSecurityGroup -ResourceGroupName $vm.ResourceGroupName | Remove-AzNEtworkSecurityGroup -Force
```

5. Delete the public IP address
```powershell
Get-AzPublicIpAddress -ResourceGroupName $vm.ResourceGroupName | Remove-AzPublicIpAddress -Force
```


# Scripts in Azure PowerShell

A PowerShell script is a text file containing commands and control constructs. The commands are invocations of cmdlets. The control constructs are programming features like loops, variables, parameters, comments, etc., supplied by PowerShell.

PowerShell script files have a .ps1 file extension. You can create and save these files with any text editor.

🈸 You can use: Windows PowerShell ISE as IDE

Once the Script is written: 

```powershell
.\myScript.ps1
```

## PowerShell techniques

### Variables

```powershell
$loc = "East US"
$iterations = 3
```

Variables can hold objects: 

```powershell
$adminCredential = Get-Credential
```

To obtain the value stored in a variable use the **$** prefix.

```powershell
$loc = "East US"
New-AzResourceGroup -Name "MyResourceGroup" -Location $loc
```

### Loops

PowerShell has several loops: **For, Do...While, For...Each,** and so on. The For loop is the best match for our needs, because we will execute a cmdlet a fixed number of times.

```powershell
For ($i = 1; $i -lt 3; $i++)
{
    $i
}
```

### Parameters

Yo can pass arguments on the command line. 

```powershell
.\setupEnvironment.ps1 -size 5 -location "East US"
```

Inside the script:
```powershell
param([string]$location, [int]$size)
```

You can omit the names:
```powershell
.\setupEnvironment.ps1 5 "East US" 
```

So inside the script you will relay on the **position** for matching the parameters unnamed. 

