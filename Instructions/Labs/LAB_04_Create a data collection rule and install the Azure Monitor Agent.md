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

- Install the Azure Monitor Agent.
  
- Configure data sources and destinations.

- Select data source types and data to collect.

- Choose a data delivery destination.

## Exercise instructions 

### Create and define a Data Collection Rule, and install the Azure Monitor Agent.

>**Note**: Create the data collection rule in the same region as your Log Analytics or Azure Monitor workspace. You can associate it with machines or containers from any subscription or resource group within the tenant. The Azure Monitor Agent will be automatically installed on Azure virtual resources.

1. In the search box at the top of the portal, enter **data collection rules**. Select **Data collection rules** in the search results.
  
2. Select **+ Create**.
  
   ![image](https://github.com/user-attachments/assets/99b9ac51-f2f4-466f-80bb-79d74874b573)

3. On the **Basics** page of the **Create Data Collection Rule** blade, specify the following settings (Leave the others at their default values):

    |Setting|Value|
    |---|---|
    |**Rule details**|
    |Rule Name|**dcr-1**|
    |Subscription|Select you subscription.|
    |Resource group|**az-rg-1**|
    |Region|**East US**|
    |Platform Type|**Windows**|
    |Data Collection Endpoint|Leave the default setting as none.|

    ![image](https://github.com/user-attachments/assets/35c527cf-499d-44b9-966f-0114b8643ef2)

4. Click the button at the bottom of the **Basics** page labeled **Next: Resources > to proceed.**
   
5. On the **Resources** page, select **+ Add resources.**

    ![image](https://github.com/user-attachments/assets/6aabf2c9-bea2-47c1-9b0b-bf131cdec4e3)

6. In the **Select a scope** template, check the **Subscription** box in the **Scope.**

    ![image](https://github.com/user-attachments/assets/2215e8cd-5047-4fc6-91ba-b2c645571bbd)

7. At the bottom of the **Select a scope** template, click **Apply.**
  
8. At the bottom of the **Resources** page, select **Next: Collect and deliver >.**

    ![image](https://github.com/user-attachments/assets/717226c3-5ce0-454f-93a4-11b0e67d5a23)

9. On the **Collect and deliver page**, click **+ Add data source.**

    ![image](https://github.com/user-attachments/assets/0809cf5b-a460-40d1-8508-e42ba7ce78c1)

10. On the **Add data source** template, under **Data source type**, select the following settings.
    
    |Setting|Value|
    |---|---|
    |**Add data source**|
    |Select which data source type and the data to collect for your resource(s).|
    |Data source type*|**Windows Event Logs**|
    |Choose Basic to to enable collection of event logs.|
    |Configure the event logs and levels to collect:|
    |Application|**Critical**, **Error**, **Warning**|
    |Security|**Audit success**, **Audit failure**|
    |System|**Critical**, **Error**, **Warning**|

    ![image](https://github.com/user-attachments/assets/5bc891ea-8cef-4baa-95c4-a432364179b1)

12. At the bottom of the **Add data source** template, select **Next: Destination >.**
   
13. In the **Add data source** template, under the **Destination** tab, select the following settings.
    
    |Setting|Value|
    |---|---|
    |**Add data source**|
    |Destination|**+ Add destination**|
    |Destination type|**Azure Monitor Logs**|
    |Subscription|Select your Subscription.|
    |Destination Details|**azwrkspc1a (az-rg-1**)|

    ![image](https://github.com/user-attachments/assets/e00c17c8-5a70-4caa-8504-92f482cc5e57)

14. At the bottom of the **Add data source** template, select **Add data source.**

    ![image](https://github.com/user-attachments/assets/4277089c-971c-4334-a49d-6ac6bfe93ff4)

15. At the bottom of the **Collect and deliver** page, select **Review + create.**

    ![image](https://github.com/user-attachments/assets/0235fed9-6309-444c-9269-b9dbd1118b63)

16. At the bottom of the **Review + create** page, select **Create.**

> **Results**: You have created a data collection rule and installed the Azure Monitor Agent.
