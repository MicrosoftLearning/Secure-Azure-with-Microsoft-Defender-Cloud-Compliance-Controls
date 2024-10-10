---
lab:
    title: 'Exercise 04 - Create a data collection rule and install the Azure Monitor Agent'    
    module: 'Module 05 - Create a data collection rule and install the Azure Monitor Agent'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


Data Collection Rules (DCRs) specify the data to be collected, while the Azure Monitor Agent applies these rules to gather logs and metrics from virtual machines in Azure, other clouds, or on-premises. Together, they enable consistent and centralized monitoring across different environments.

---

## Skilling tasks

- Create and define a Data Collection Rule.

- Select target resources for data collection.
  
- Configure data sources and destinations.

- Select data source types and data to collect.

- Choose a data delivery destination.

## Exercise instructions 

### Create and define a Data Collection Rule.

>**Note**: Create your data collection rule in the same region as your destination Log Analytics workspace or Azure Monitor workspace. You can associate the data collection rule to machines or containers from any subscription or resource group in the tenant. 
   
1. In the search box at the top of the portal, enter Data collection rules. Select Data collection rules in the search results.

2. Select **+ Create**.






4. On the **Basics** tab of the **Create Data Collection Rule** blade, specify the following settings (leave others with their default values):

    |Setting|Value|
    |---|---|
    |**Rule details**|
    |Rule Name|**dcr-1**|
    |Subscription|the name of the Azure subscription you are using in this lab|
    |Resource group|**az-rg-1**|
    |Region|**East US**|
    |Platform Type|**Windows**|
    |Data Collection Endpoint|*Leave the default of none*|

   ![image](https://github.com/user-attachments/assets/eee884f6-b20f-4d51-9310-6e755746ed9a)

   

6. Select **Review + create**.

7. On the **Review + create** tab of the **Create Log Analytics workspace** blade, select **Create**.




3.
4. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
5. From Defender for Cloud's menu, open **Environment settings.**

6. Select the your subscription.

7. In the Settings & monitoring Coverage column of the Defender plans, select **Settings & monitoring.**

8. In the Log Analytics row, in the Configuration column, click **Edit configuration.**

9. In the Auto-provisioning configuration template complete the following actions:

   - Under Workspace selection, click **Custom workspace.**

   - Click the **dropdown menu** and **select** your previously created workspace.

   - Under **Security events storage**, click the **dropdown menu** and, select **All Events.**

   - At the bottom of the Auto-provisioning template, click **Apply.**
   
![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/c1c812e7-b5ca-4caa-b8e6-34a6e4b325fd)




> **Results**: You have configured the Log Analytics agent and workspace in Microsoft Defender for Cloud.
