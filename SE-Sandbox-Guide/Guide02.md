# 2. Rapid Prototyping

Rapid Prototyping turns your exported whiteboard into deployment assets. The deck offers two options. Groups run Option 1, may use Option 2 if they prefer to work in VS Code.

## Option 1: Rapid Prototyping with Cora

Use Cora in the CAIP Technical Workshop Web App to transform a future-state architecture into a working solution prototype — generating the solution accelerator recommendation, Bicep templates, deployment assets, synthetic data, and execution guidance. This is useful for demonstrating how the proposed architecture can be quickly translated into a deployable Sandbox environment.

### How to use it:

1. In the CAIP Technical Workshop Web App, upload your future-state architecture image (or the reference architecture as a backup) to Cora, with a natural-language prompt describing it.
1. Ask Cora to explain the architecture and recommend a solution accelerator.
1. Generate the Bicep template, deployment assets, synthetic data, and an execution guide.
1. Download the assets and open them in VS Code to review with GitHub Copilot.
1. Validate the assets, then deploy to the sandbox.
1. Review the deployed environment and confirm your business challenges are addressed.


### Steps: Access the Cloud & AI Platform Technical Workshops web application

### `Steps to navigate to CAIP Tech Workshop Web App.`

1. Click on the **Microsoft Edge** from the Lab VM desktop.
   
   ![](../SE-Sandbox-Guide/media/amp8.png)
   
1. Right click on [Cloud & AI Platform Technical Workshops](https://caip-tech-workshops.azurewebsites.net/), then select **Copy link** and then paste the link on the Web browser.

1. Login with the following credentials:

    - Username: **<inject key="AzureAdUserEmail"></inject>**
    - Password: **<inject key="AzureAdUserPassword"></inject>**

1. After the application loads, you will see the workshop site home page as shown below.

   ![Step701](../SE-Sandbox-Guide/media/cd18.png)

1. Select the **Modernize with confidence** to explore the available outcomes and workshop scenarios.

   ![Step701](../SE-Sandbox-Guide/media/se26.png)

1. On the right side of the page, you'll find **Cora**, the AI-Powered Rapid Prototyping Copilot. Use the chat interface to enter prompts and interact with the workshop outcomes and scenarios as follows:

   - From the left navigation pane, under **Outcomes**, select **Modernize Faster with Agentic AI (1)**.
   - Under **Scenarios**, select **Agentic App & Databases Modernization (2)**.
   - In the **Technical Workshops** section, expand **Prototype using Cora (3)** and select **Cora (Preview) for Roadshows (4)**.
   
     ![Step001](../SE-Sandbox-Guide/media/se27.png)

1. Continue in the **Cora Chat** pane for **Rapid Prototyping**.  

   ![Step001](../SE-Sandbox-Guide/media/se37.png)

1. In Cora chat pane, copy and paste the following business problem statement to Cora. 

   ```
   My customer Caldova is a pharmaceutical manufacturer who plans to launch their new V2 product. I have three comments 

   1) Caldova’s supply chain planning application runs on legacy .NET, the manufacturing database sits on an on-premises SQL Server. It’s Data remains siloed across IoT, supply chain, customer, production, supplier, and manufacturing systems. Recommend a solution to migrate the on-premises SQL Server to Azure SQL DB. 

   2) Also, Caldova currently can manufacture 100 million units in 6 months. It needs to ensure the ability to manufacture 107 million units in 6 months, a gap of 7% manufacturing capacity. The closure of the 7% capacity gap across three manufacturing plants is needed to support the upcoming V2 product across multiple plants. Caldova needs to understand whether it can close the gap internally, and if not, which pre-qualified contract manufacturing organizations can fast-track support in a 3–6-month window. 

   3) They want an AI-powered multi-agent solution using Microsoft Fabric and Microsoft Foundry to identify internal improvements to their manufacturing plants as well as recommend contract manufacturing orgs to achieve the desired production capacity.
   ```

1. From the Cora chat, select the Attach file **(1)** icon, then navigate to `C:\miq-project` folder **(2)**, select the name as **Future-State-Architecture (3)** and then **Open (4)**.

   ![Step12](../SE-Sandbox-Guide/media/se38.png) 

1. Along with the final `Future State Architecture` screenshot from `C:\miq-project` folder and copy & paste the following statement on Cora. 

   ```
   Explain this Architecture.
   ``` 

   ![Step001](../SE-Sandbox-Guide/media/cd10.png)   

1. Review the Architecture Summary provided by Cora.

   ![Step001](../SE-Sandbox-Guide/media/cd11.png)   

1. **Copy & paste** the following statement on Cora.

   ```
   Generate Synthetic Data
   ```

   ![Step001](../SE-Sandbox-Guide/media/cd12.png)  

    >**Note:** It might take 2-3 minutes to generate the data.

1. Review the tables from the generated data and click on **Download full artifacts.**      

   ![Step001](../SE-Sandbox-Guide/media/se40.png)  

1. Copy and paste the following prompt on Cora: 

   ```
   Generate the deployment artifacts using this Architecture.
   ```

   ![Step001](../SE-Sandbox-Guide/media/cd14.png) 

    >**Note:** It might take 1-2 minutes to generate the Deployment artifacts

1. Review the generated files from the Cora and click on **Download** to download the zip file on top left. 

   ![Step001](../SE-Sandbox-Guide/media/se39.png) 

1. Save the Downloaded zip file in your preferred location.   

   ![Step001](../SE-Sandbox-Guide/media/cd16.png)

1. Click on the prompt `Generate the prototype guide using this context`. It will generate the Exercises in the left. 

   ![Step001](../SE-Sandbox-Guide/media/se41.png)

#### Multi-Agent Solution to Test

The rapid prototype should include the following agents:

- Orchestrator / Supervisor
- Current capacity analysis agent
- Contract manufacturer analysis agent
- COO recommender agent
- Compliance guardrail agent

1. Navigate to your downloaded zip file and extract the folder.

1. Navigate to the **VS Code** from Lab VM.

1. Open the Extracted folder.

1. Send the below prompt in the GitHub Copilot Chat.

### Deployment Prompt

```
You are an Azure Cloud Architect and DevOps Engineer.

I have all solution artifacts in this repository. Analyze the repository and deploy the complete solution into my Azure tenant.

Tasks:

1. Review all artifacts and identify:
   - Infrastructure as Code (Bicep, ARM, Terraform)
   - Application code
   - Azure resources required
   - Configuration files
   - Deployment dependencies

2. Create a deployment plan before executing:
   - Resource Groups
   - Networking
   - Storage Accounts
   - Key Vaults
   - Microsoft Fabric integrations
   - Microsoft Foundry
   - Azure OpenAI
   - Azure Functions
   - App Services
   - SQL Databases
   - Any other required resources

3. Validate:
   - Resource naming conventions
   - RBAC permissions
   - Managed identities
   - Environment variables
   - Secrets and Key Vault references
   - Cost estimates
   - Azure Policy compliance

4. Generate:
   - deployment.md
   - architecture.md
   - deploy.sh
   - deploy.ps1
   - GitHub Actions workflow

5. Deploy the solution to Azure using best practices:
   - Create resource group if it does not exist
   - Provision infrastructure
   - Configure networking and security
   - Deploy applications
   - Configure monitoring and logging
   - Validate deployment health

6. After deployment provide:
   - Deployed resource inventory
   - Resource IDs
   - URLs and endpoints
   - Validation results
   - Any deployment issues and resolutions

Azure Details:
- Tenant ID: <inject key="TenantID" enableCopy="true"/>
- Subscription ID: <inject key="SubscriptionID" enableCopy="true"/>
- Resource Group: rg-cora
- Region: westus2

Do not make assumptions.
Ask for missing information.
Use Azure CLI and Bicep wherever possible.
Follow Microsoft Well-Architected Framework and security best practices.
```


## This completes the Rapid Prototyping using Cora.

### Now, click on **`Next >>`** from the lower right corner to experience **`Rapid Prototyping using GitHub Copilot`**.
