# Section 3: Define Azure SQL Database Resources

In this section, we'll define the resources needed to create an Azure SQL Database and its dependencies using Pulumi and TypeScript.

1. **Import Necessary Modules:** 

    Open the `index.ts` file in the `azure-ts` directory. At the top of the file, you'll need to import the required Pulumi and Azure modules:


```typescript
import * as vznAzNative from '@vizientinc/pulumi-azure-native';
import { ResourceGroupVzn } from '@vizientinc/pulumi-azure-native/lib/resources/ResourceGroupVzn';
import { authorization } from '@pulumi/azure-native';
import {Naming as VizNaming, sql} from '@vizientinc/pulumi-azure-native';
```

***ATTENTION:*** 

*Notice we are importing the Vizient Pulumi Azure module. This module is a wrapper around the official Pulumi Azure module.*
