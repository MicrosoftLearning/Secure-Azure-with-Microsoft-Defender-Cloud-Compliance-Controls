---
lab:
    title: 'Exercise 02 - Create a workspace'
    module: 'Module 02 - Create a Log Analytics workspace for Microsoft Defender for Cloud'
---

>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 

When you collect logs and data, the information is stored in a workspace. A workspace has a unique workspace ID and resource ID. The workspace name must be unique for a given resource group. After you've created a workspace, configure data sources and solutions to store their data there. 

---

## Skilling task

- Create a Log Analytics workspace.
- Associate the workspace with an existing resource group.
- Specify a specific region to deploy the workspace.

## Exercise instructions 

### Use the Log Analytics workspaces menu to create a workspace.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. From the Azure portal menu, enter **Log Analytics** in the search box. As you begin typing, the list filters based on your input. Select **Log Analytics workspaces.**

4. Select **Create.**

5. On the **Basics** tab of **Create Log Analytics workspace,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Enter **azure-rg-1.** Select **OK**|
   |**Instance details**|
   |Name|Enter **azwrkspc1a.**|
   |Region|Select **East US.**|

6. Select the **Review + create tab,** or select the blue Review + create button at the bottom of the page.
  
8. Select **Create.**

> **Results:** You have created a Log Analytics workspace, to collect data from Azure reources, and diagnostics or log data from Azure Storage.
