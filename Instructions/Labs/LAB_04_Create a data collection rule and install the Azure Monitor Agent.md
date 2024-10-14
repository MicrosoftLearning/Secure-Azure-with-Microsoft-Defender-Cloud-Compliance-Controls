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
   
1. In the search box at the top of the portal, enter data collection rules. Select Data collection rules in the search results.

2. Select **+ Create**.

![image](https://github.com/user-attachments/assets/99b9ac51-f2f4-466f-80bb-79d74874b573)

3. On the **Basics** tab of the **Create Data Collection Rule** blade, specify the following settings (leave others with their default values):

    |Setting|Value|
    |---|---|
    |**Rule details**|
    |Rule Name|**dcr-1**|
    |Subscription|the name of the Subscription you are using in this lab|
    |Resource group|**az-rg-1**|
    |Region|**East US**|
    |Platform Type|**Windows**|
    |Data Collection Endpoint|*Leave the default of none*|

![image](https://github.com/user-attachments/assets/35c527cf-499d-44b9-966f-0114b8643ef2)

4. Click on the button labeled **Next: Resources >** to proceed.

5. On the Resources tab, select **+ Add resources**.
  
>**Note**: The Azure Monitor Agent will automatically be installed on the virtual machines (resources) selected to collect data.

![image](https://github.com/user-attachments/assets/47174eb4-4343-49a2-b49d-e9dee76787e4)

6. In the Select a scope template, check the **Subscription** box in the Scope selection, and click **Apply.**

![image](https://github.com/user-attachments/assets/2215e8cd-5047-4fc6-91ba-b2c645571bbd)

7. At the bottomn of the **Resources** page, select **Next: Collect and deliver**. 


![image](https://github.com/user-attachments/assets/717226c3-5ce0-454f-93a4-11b0e67d5a23)


![image](https://github.com/user-attachments/assets/0809cf5b-a460-40d1-8508-e42ba7ce78c1)


![image](https://github.com/user-attachments/assets/5bc891ea-8cef-4baa-95c4-a432364179b1)


![image](https://github.com/user-attachments/assets/4277089c-971c-4334-a49d-6ac6bfe93ff4)


![image](https://github.com/user-attachments/assets/4a54278c-2bee-4717-98a6-136f4c4d41e2)






8. Select **Review + create**.








> **Results**: You have created a data collection rule and install the Azure Monitor Agent.
