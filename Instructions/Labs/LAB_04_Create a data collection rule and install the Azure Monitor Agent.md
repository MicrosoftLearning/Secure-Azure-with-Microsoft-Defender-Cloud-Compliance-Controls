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

![image](https://github.com/user-attachments/assets/e428c441-9d8d-4460-acd9-a97e2aa2b5af)

3. On the **Basics** tab of the **Create Data Collection Rule** blade, specify the following settings (leave others with their default values):

    |Setting|Value|
    |---|---|
    |**Rule details**|
    |Rule Name|**dcr-1**|
    |Subscription|the name of the Iginte subscription you are using in this lab|
    |Resource group|**az-rg-1**|
    |Region|**East US**|
    |Platform Type|**Windows**|
    |Data Collection Endpoint|*Leave the default of none*|

![image](https://github.com/user-attachments/assets/eee884f6-b20f-4d51-9310-6e755746ed9a)   

4. Click on the button labeled **Next: Resources >** to proceed.



5. On the Resources tab, select **+ Add resources**.

![image](https://github.com/user-attachments/assets/619106b4-7f5e-44dd-98c7-129689ab89c0)


![image](https://github.com/user-attachments/assets/c95b76cd-1515-47a5-b07b-02dcb28c0bf3)


7.


8. Select **Review + create**.

9. On the **Review + create** tab of the **Create Log Analytics workspace** blade, select **Create**.






> **Results**: You have created a data collection rule and install the Azure Monitor Agent.
