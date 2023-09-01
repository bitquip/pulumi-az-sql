# Define Resources for Configuration
    
Next, we'll define some resources to hold configuration values.
These configuration values are common to all resources and will be referenced throughout the project.

***Resource Tags***

```typescript
const tags = {
    env: 'sandbox',
    app: 'azure-sql',
    servicetier: 't1',
    owneremail: 'your_email@your_domain.com'
};
```

| Tag          | Description                                      |
|--------------|--------------------------------------------------|
| env          | The environment in which the resource is being created. This is typically one of the following values: <br> **sandbox, dev, sandbox01, dev01, nonprod, preprod, prod, prod01**. |
| app          | The name of the application the resource is being created for. This is typically a string. |
| servicetier  | The service tier of the resource. This is typically one of the following values: t1, t2, t3, t4. |
| owneremail   | The email address of the resource owner. This is typically a string. |



Tags provide a way to associate metadata with Azure resources, such as virtual machines, storage accounts, databases, and more. 

These tags consist of name-value pairs and are particularly useful for organizing, categorizing, and managing resources within an Azure environment/subscription.

When creating resources at Vizient, we use a standard set of tags to help us organize and manage our resources. These tags are defined in the `tags` object above.

***Infrastructure Configuration***

```typescript
const infraConfigs = {
    subscriptionId: 'your_subscription_id'
    aseId: "",
    instance: '01',
    region: 'eastus2',
};
```

While the `tags` object is used to reference necessary values common to all resources, the `infraConfigs` object is used to reference values specific to the infrastructure configurations.


| Field         | Description                                                      |
|---------------|------------------------------------------------------------------|
| subscriptionId| The ID of the Azure subscription in which the resource is being created. This is typically a GUID. |
| aseId         | The ID of the Azure App Service Environment in which the resource is being created. This is typically a GUID. |
| instance      | The instance of the resource being created. This is typically a number. |
| region        | The Azure region in which the resource is being created. This is typically a string. |


***Role Configuration***

```typescript
interface RoleConfigs {
    devRoleGroupId: vznpulumi.pulumi.Input<string>;
    devRoleGroupName: string;
    t1RoleGroupId: vznpulumi.pulumi.Input<string>;
    t1RoleGroupName: string;
    apiDbRoles: Array<string>;
}
```

The `RoleConfigs` interface is used to define the role configurations. These configurations are used to manage access to the resources within the resource group.

| Field              | Description                                                                                             | 
|--------------------|---------------------------------------------------------------------------------------------------------|
| devRoleGroupId     | The ID of the Azure Active Directory group that will be used to manage the resource group. This is typically a GUID. |
| devRoleGroupName   | The name of the Azure Active Directory group that will be used to manage the resource group. This is typically a string. |
| t1RoleGroupId      | The ID of the Azure Active Directory group that will be used to manage the resource group. This is typically a GUID. |
| t1RoleGroupName    | The name of the Azure Active Directory group that will be used to manage the resource group. This is typically a string. |
| apiDbRoles         | The roles that will be assigned to the Azure Active Directory group that will be used to manage the resource group. This is typically an array of strings. |
