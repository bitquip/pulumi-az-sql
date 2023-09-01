## Section 4: Deploy the Resources

***With the resources defined, it's time to deploy them:***

1. **Deploy:** 

    Save the changes you made to the `index.ts` file.

    Before we run the command to actually deploy the resources, let's take a look at some of the commands frequently used with Pulumi before we deploy the resources:

    ***pulumi stack select***

    ```bash
    pulumi stack select
    ```
    
     If you have multiple stacks, you can use this command to select the stack you want to deploy to. 


    ***pulumi refresh***

    ```bash
    pulumi refresh
    ```

    This command will refresh the current state of the stack. This should be run after changes are made to the stack outside of Pulumi. For example, if you were to manually delete a resource in Azure, you would need to run this command to update the state of the stack.

    It should run automatically when performing a `pulumi up` but it's good to know how to run it manually.

    ***pulumi preview***

    ```bash
    pulumi preview
    ```

    This command will show you a preview of the changes that will be made to your stack. This is useful if you want to see what changes will be made before you deploy them. 

    ***Deploying***

    In your terminal, navigate to the root of your project directory and run the following command:

    ```bash
    pulumi up
    ```

    Pulumi will analyze your code, create a deployment plan, and prompt you to confirm the changes before proceeding.

2. **Review and Confirm:**

After reviewing the proposed changes, type `yes` to confirm and initiate the deployment.

3. **Observe Outputs:**

Once the deployment is complete, Pulumi will display outputs, including connection strings for the SQL Server and Database. These outputs are crucial for connecting to your newly created resources.