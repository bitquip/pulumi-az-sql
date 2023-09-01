# Define SQL Server
    
**Now, let's define an Azure SQL Server:**

```typescript
const sqlServer = new sql.ServerVzn(
  'sqlServer',
  {
    appInfo: {
      region: location,
      resourceGroupName: resourceGroup.name,
      serviceTier: serviceTier,
      tags: tags,
    },
    resourceName: VizNaming.SqlServer(app, env, location, instance),
    allowAllAzureTraffic: false,
    allowedVizientLocations: [
      LocationCode.cap,
      LocationCode.ae2,
    ],
    allowedSubnetIDs: vnetIDsSql2Allow,
    subscriptionId: subscriptionId,
    tenantId: tenantId,
  },
  {
    protect: false,
  }
);
```

In this code, we are creating an Azure SQL Server named `sqlServer` in the `eastus2` region. 

We are also associating the SQL Server with the `azure-sql` application, the `sandbox` environment, and the `t1` service tier.

The `Server` resource allows you to define the following properties:

| Field                  | Description                                                                                             |
|------------------------|---------------------------------------------------------------------------------------------------------|
| appInfo                | The application information associated with the SQL Server. This is typically an object containing the application name, environment, service tier, and tags. |
| resourceName           | The name of the SQL Server. This is typically a string. The `VizNaming.SqlServer` method is used to generate the name of the SQL Server. |
| allowAllAzureTraffic   | A boolean value indicating whether or not to allow all Azure traffic to the SQL Server. This is typically a boolean value. |
| allowedVizientLocations| An array of Azure locations that are allowed to access the SQL Server. This is typically an array of strings. |
| allowedSubnetIDs       | An array of Azure subnet IDs that are allowed to access the SQL Server. This is typically an array of strings. |
| subscriptionId         | The ID of the Azure subscription in which the SQL Server is being created. This is typically a GUID. |
| tenantId               | The ID of the Azure Active Directory tenant in which the SQL Server is being created. This is typically a GUID. |
