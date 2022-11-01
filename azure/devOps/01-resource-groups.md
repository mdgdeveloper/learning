# Resource Groups
[Resources](02-resources.md) are any type of element that is involved in the deployment of the infrastructure. 

**Resource group**: Logical collection of all of your resources dedicated for a defined purpose. 


## Process
In Azure Portal: Search and select **Resource Groups**:

Resource Groups > + Add

Enter the following values:
- **Subscription**
- **Resource Group** The resource group name 
- **Region** Azure Location 

Once created we can apply access control system to manage the access to all the resources. 
We can add to that resource group the VMs, Virtual Network or other type of resource we consider.

> 🚨 Tags can be added at that stage and provide support for billing and access control. 

When the resource group is created, in the process of creating a new resource, such as VMs, you can provide the resource group to which will be added. 

## Azure Resource Manager (ARM)
Platform that allows the admin to manage the assets. 

> 🚨 Resource groups can only be managed using the **Azure Portal** or **PowerShell**

## References
- https://www.youtube.com/watch?v=hPxPLp5f-6g&t