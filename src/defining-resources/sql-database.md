# Define SQL Database

**Next, define an Azure SQL Database within the SQL Server:**

```typescript
 new sql.DatabaseVzn(
  'sqlDatabase',
  {
    createAADGroupsInSandbox: true,
    resourceName: 'sqldatabase',
    server: sqlServer.sqlServer, // notice we are using the sqlServer object created above
    databaseSku: {
      name: daasDbDTU,
    },
    maxSizeInGiB: 100,
    appInfo: {
      region: location,
      resourceGroupName: resourceGroup.name,
      tags: tags,
      serviceTier: serviceTier,
    },
  },
  {
    parent: sqlServer.sqlServer,
    dependsOn: sqlServer.sqlServer,
  }
);
```

In this code, we are creating an Azure SQL Database named `sqlDatabase` in the `eastus2` region. We are also associating the SQL Database with the `azure-sql` application, the `sandbox` environment, and the `t1` service tier.

The `Database` resource allows you to define the following properties:  

| Field                      | Description                                                                                             |
|----------------------------|---------------------------------------------------------------------------------------------------------|
| createAADGroupsInSandbox   | A boolean value indicating whether or not to create Azure Active Directory groups in the sandbox environment. This is typically a boolean value. |
| resourceName               | The name of the SQL Database. This is typically a string. |
| server                     | The SQL Server in which the SQL Database is being created. This is typically a SQL Server object. Notice that we are using the `sqlServer` object created above. |
| databaseSku                | The SKU of the SQL Database. This is typically an object containing the name of the SKU. The `daasDbDTU` variable is used to define the name of the SKU. |
| maxSizeInGiB               | The maximum size of the SQL Database in gigabytes. This is typically a number. |
| appInfo                    | The application information associated with the SQL Database. This is typically an object containing the application name, environment, service tier, and tags. |
