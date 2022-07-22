# Azure Resource Manager benefits 
Azure Resource Manager enables you to work with the resources in your solution as a group. 

- Deploy
- Update
- Delete

You use a template for deployment and that template can work for different environments such as testing, staging, and production. 

Azure Resource Manager provides
- Security
- Auditing
- Tagging 


## Consistent Management Layer 

Azure Resource Manager provides a consistent management layer to perform tasks through:
- Azure PowerShell
- Azure CLI
- Azure portal
- REST API
- Client SDKs

## Benefits:

- Deploy, manage, and monitor all the resources for your solution **as a group**
- Repeatedly deploy the solution throughout the development lifecycle
- Manage infrastructure through declarative templates.
- Define dependencies between resources 
- Access control to all services in your resource group: Role-Based Access Control (RBAC)
- Apply tags
- Clarify billing 


## Guidance: 

Suggestion that may help:

- Define and deploy the infrastructure through the declarative syntax in Azure Resource Manager templates.
- Define all deployment and configuration steps in teh template. Avoid manual steps. 
- Run imperative commands to manage the resources: start or stp an app or machine.
- Arrange resources with the same lifecycle in a resource group.
- Use tags for all other organizing of resources.

# Azure resource terminology

- **Resource**: A manageable item that is available through Azure. (e.g.: VM, storage account, web app, database, virtual network)
- **Resource group**: A container that holds related resources for an Azure solution. The resource group can include all the resources for the solution, or only those resources that you want to manage as a group. You decide how you want to allocate resources to resource groups based on what makes the most sense for your organization.
- **Resource provider**: A service that supplies the resources you can deploy and manage through Resource Manager. Each resource provider offers operations for working with the resources that are deployed.(e.g.: Microsoft.Storage, Microsoft.Web)
- **Template**: A JSON file that defines one or more resources to deploy to a resource group. It also defines the dependencies between the deployed resources. The template can be used to deploy the resources consistently and repeatedly.
- **Declarative syntax**: Syntax that lets you state "Here is what I intend to create" without having to write the sequence of programming commands to create it. The Resource Manager template is an example of declarative syntax. In the file, you define the properties for the infrastructure to deploy to Azure.

## Resource providers
Each resource provider offers a set of resources and operations for working with an Azure service. 

Example: for keys => Microsoft.KeyVault 

The name of a resource type is in the format: {resource-provider}/{resource-type}.

# Create resource groups 

Deployment of resources to a resource group becomes a job where you can track the template execution. If deployment fails, the output of the job can describe why the deployment failed. 

Deployments are incremental; if a resource group contains two web apps and you decide to deploy a third, the existing web apps will not be removed.

## Considerations
Resource Groups are at their simplest a logical collection of resources. There are a couple of small rules for resource groups:

- Resources can only exist in one resource group.
- Resource Groups cannot be renamed.
- Resource Groups can have resources of many different types (services).
- Resource Groups can have resources from many different regions. 

## Creating resource groups

When defining the resource group:
- All the resources in your group should share the same lifecycle. 
- Each resource can only exist in one resource group.
- You can add or remove a resource to a resource group at any time.
- You can move a resource from one resource group to another group.
- A resource group can contain resources that reside in different regions. 
- A resource group can be used to scope access control for administrative actions.
- A resource can interact with resources in other resources groups. 

When creating a resource group, you need to provide a location for that resource group. 

For compliance reasons, you may need to ensure that your data is stored in a particular region.

# Create Azure Resource Manager locks 

A common concern with resources provisioned in Azure is the ease with which they can be deleted. 

Resource Manager locks allow organizations to put a structure in place that prevents the accidental deletion of resources in Azure.

- You can associate the lock with a subscription, resource group or resource.
- Locks are inherited by child resources. 

## Lock types

- Read-Only locks, which prevent any changes to the resource.
- Delete locks, which prevent deletion.

# Reorganize Azure Resources 

Use Case: Move resources to either a new subscription or a new resource group in the same subscription.

When moving resources, both the source group and the target group are locked during the operation. Write and delete operations are blocked on the resource groups until the move completes.

The resources are still available. 

## Limtations

There is a page to consult if an specific type of resource can be moved and what type of movement is allowed for it. 

## Implementation

To move resources, select the resource group containing those resources, then select the **Move** button. Select the resources to move and the destination resource group. 

Acknoeledge that you need to update scripts. 

# Remove resources and resource groups. 

Deleting a resource group deletes all the resources contained within it. That resource group might contain resources that resources in other resource groups depend on.

## Using PowerShell to delete resource groups

To remove a resource group use, Remove-AzResourceGroup. 

```
Remove-AzResourceGroup -Name "ContosoRG01" 
```

## Removing resources 

You can also delete individual resources within a resource group. 

# Determine resource limits

Azure lets you view resource usage against limits. This is helpful to track current usage, and plan for future use.

- The limits shown are the limits for your subscription.
- When you need to increase a default limit, there is a Request Increase link.
- All resources have a maximum limit listed in Azure limits.
- If you are at the maximum limit, the limit can't be increased.

