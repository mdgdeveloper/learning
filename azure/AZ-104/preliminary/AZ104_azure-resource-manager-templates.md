# Azure Resource Manager Templates

## Templates
Defines all the Resource Manager resources in a deployment. 

You can deploy a Resource Manager template into a resource group as a single operation.

## Benefits 

- **Templates improve consistency.** Resource Manager templates provide a common language for you and others to describe your deployments. Regardless of the tool or SDK that you use to deploy the template, the structure, format, and expressions inside the template remain the same.
- **Templates help express complex deployments.** Templates enable you to deploy multiple resources in the correct order. For example, you wouldn't want to deploy a virtual machine prior to creating an operating system (OS) disk or network interface. Resource Manager maps out each resource and its dependent resources, and creates dependent resources first. Dependency mapping helps ensure that the deployment is carried out in the correct order.
- **Templates reduce manual, error-prone tasks.** Manually creating and connecting resources can be time consuming, and it's easy to make mistakes. Resource Manager ensures that the deployment happens the same way every time.
- **Templates are code.** Templates express your requirements through code. Think of a template as a type of Infrastructure as Code that can be shared, tested, and versioned similar to any other piece of software. Also, because templates are code, you can create a "paper trail" that you can follow. The template code documents the deployment. Most users maintain their templates under some kind of revision control, such as GIT. When you change the template, its revision history also documents how the template (and your deployment) has evolved over time.
- **Templates promote reuse.** Your template can contain parameters that are filled in when the template runs. A parameter can define a username or password, a domain name, and so on. Template parameters enable you to create multiple versions of your infrastructure, such as staging and production, while still using the exact same template.
- **Templates are linkable.** You can link Resource Manager templates together to make the templates themselves modular. You can write small templates that each define a piece of a solution, and then combine them to create a complete system.
- **Templates simplify orchestration**. You only need to deploy the template to deploy all of your resources. Normally this would take multiple operations.

## Template schema

Azure Resource Manager templates are written in **JSON**. 

Example:

```json
{
    "$schema": "http://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "",
    "parameters": {},
    "variables": {},
    "functions": [],
    "resources": [],
    "outputs": {}
}
```

| Element name | Required | Description |
| - | :-: | - | 
| $schema | yes | Location of the JSON schema file that describes the version of the template language. | 
| contentVersion | yes | Version of the template. Use this value to document significant changes in your template.| Entered by the user |
| parameters | no | Values that are providen when deplpoyment is executed to customize resource deployment | 
| variables | no | Values that are used as JSON fragments in the template to simplify template language expressions | 
| functions | no | User-defined fucntions that are available within the template | 
| resources | yes | Resource types that are deployed or updated in a resource group | 
| outputs | no | Values that are returned after deployment | 

### Template parameters 

In the parameters section of the templpate, you specify which values you can input when deplpoying the resources. 

The available properties for a parameter: 

```json
"parameters": {
    "<parameter-name>" : {
        "type" : "<type-of-parameter-value>",
        "defaultValue": "<default-value-of-parameter>",
        "allowedValues": [ "<array-of-allowed-values>" ],
        "minValue": <minimum-value-for-int>,
        "maxValue": <maximum-value-for-int>,
        "minLength": <minimum-length-for-string-or-array>,
        "maxLength": <maximum-length-for-string-or-array-parameters>,
        "metadata": {
        "description": "<description-of-the parameter>"
        }
    }
}
```


Example: 

```json

"parameters": {
  "adminUsername": {
    "type": "string",
    "metadata": {
      "description": "Username for the Virtual Machine."
    }
  },
  "adminPassword": {
    "type": "securestring",
    "metadata": {
      "description": "Password for the Virtual Machine."
    }
  }
}
```

> 🛑 You're limited to 256 parameters in a template. You can reduce the number of parameters by using objects that contain multiple properties.

## Azure Bicep templates

Azure Bicep is a domain-specific language (DSL) that uses declarative syntax to deploy Azure resources. 

You can use Bicep instead of JSON to develop your Azure Resource Manager templates (ARM templates). The JSON syntax to create an ARM template can be verbose and require complicated expressions. Bicep syntax reduces that complexity and improves the development experience. Bicep is a transparent abstraction over ARM template JSON and doesn't lose any of the JSON template capabilities.

### How it works?

Once  the Bicep template is submitted to Resource Manager, which still requires JSON templates, the tooling that's built into Bicep transpiles the Bicep template into a JSON template.

### Bicep improvements over JSON
- **Simpler syntax**
- **Modules**
- **Automatic dependency management**
- **Type validation and IntelliSense**


## QuickStart Templates

Link: [Azure QuickStart ](https://azure.microsoft.com/en-us/resources/templates/)

- The README.md file provides an overview of what the template does.
- The azuredeploy.json file defines the resources that will be deployed.
- The azuredeploy.parameters.json file provides the values the template needs.


