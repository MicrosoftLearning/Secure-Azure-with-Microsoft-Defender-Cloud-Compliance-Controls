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

### CCreate and define a Data Collection Rule.

>**Note**: Create your data collection rule in the same region as your destination Log Analytics workspace or Azure Monitor workspace. You can associate the data collection rule to machines or containers from any subscription or resource group in the tenant. 

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. From Defender for Cloud's menu, open **Environment settings.**

4. Select the your subscription.

5. In the Settings & monitoring Coverage column of the Defender plans, select **Settings & monitoring.**

7. In the Log Analytics row, in the Configuration column, click **Edit configuration.**

8. In the Auto-provisioning configuration template complete the following actions:

   - Under Workspace selection, click **Custom workspace.**

   - Click the **dropdown menu** and **select** your previously created workspace.

   - Under **Security events storage**, click the **dropdown menu** and, select **All Events.**

   - At the bottom of the Auto-provisioning template, click **Apply.**
   
![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/c1c812e7-b5ca-4caa-b8e6-34a6e4b325fd)




> **Results**: You have configured the Log Analytics agent and workspace in Microsoft Defender for Cloud.
