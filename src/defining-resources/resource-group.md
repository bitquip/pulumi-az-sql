# Define a Resource Group

Start by defining a resource group to hold your Azure resources:

```typescript
new ResourceGroupVzn(`rg-eastus2-01`, {
        appName: tags.app,
        environment: tags.env,
        serviceTier: tags.servicetier,
        owner: vznAzNative.azuread.getUser({
            userPrincipalName: tags.owneremail,
        }),
        region: infraConfigs.region,
        instance: infraConfigs.instance,
        subscriptionId: infraConfigs.subscriptionId,
        devAADGroupName: roleConfigs.t1RoleGroupName,
    }).resourceGroup;
```

The `ResourceGroup` resource represents a logical container for your resources within Azure. It helps you manage your resources as a group and apply policies to them as a group.

In this code, we are creating a resource group named `rg-eastus2-01` in the `eastus2` region. We are also associating the resource group with the `azure-sql` application, the `sandbox` environment, and the `t1` service tier.

The `ResourceGroup` resource also allows you to apply policies to the resources within the group. In this code, we are associating the resource group with the `t1` role group. This role group is used to manage access to the resources within the resource group.


| Field             | Explanation                                                                                                         |
|-------------------|---------------------------------------------------------------------------------------------------------------------|
| `appName`         | The name of the application associated with the resource group. This helps identify the purpose of the resources grouped together within this Azure Resource Group. |
| `environment`     | The environment associated with the resource group, such as 'development', 'production', 'sandbox', etc. This categorizes resources based on their intended usage environment. |
| `serviceTier`     | The service tier or level of the application associated with the resource group. It indicates the performance, features, and capabilities of the application within this group. |
| `owner`           | The owner of the resource group, typically represented by their email address. This identifies the person or team responsible for managing and maintaining the resources within the group. |
| `region`          | The Azure region where the resource group is located. This specifies the geographical location of the data center hosting the resources within this group. |
| `instance`        | The instance identifier or name associated with the resource group. It's often used to distinguish between different instances of the same application or resources, such as '01' for the first instance. |
| `subscriptionId`  | The ID of the Azure subscription to which the resource group belongs. This indicates the specific subscription under which the resources in this group are billed and managed. |
| `devAADGroupName` | The name of the Azure Active Directory group associated with development access and roles. This group might have permissions to manage resources in a development environment. |



***Attention:***
Typically you would define related resources within their own file and reference them in the main index.ts file. 
However, for the sake of simplicity, we'll define all of our resources directly in the index.ts file.

This will allow us to focus on the specific resource we're creating.
