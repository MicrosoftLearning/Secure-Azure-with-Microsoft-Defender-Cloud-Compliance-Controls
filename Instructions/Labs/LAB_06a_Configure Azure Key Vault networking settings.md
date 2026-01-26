---
lab:
    title: 'Exercise 06a - Configure Azure Key Vault networking settings'    
    module: 'Module 07 - Configure Azure Key Vault networking settings'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


You can use the Azure portal to configure the Azure Key Vault networking settings to work with other applications and Azure services. 

---

## Skilling tasks

- Create a key vault using the Azure portal.
- Add an exsiting virtual network to a firewall and virtual network rules.
- Configure a virtual network and subnet to allow access to a key vault.

### Estimated Lab Duration: 10 minutes

## Exercise instructions 

### Use the Azure portal to create an Azure Key Vault.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
  
2. In the search box at the top of the portal, enter **key vaults.** Select **Key vaults** in the search results.

3. From the results list, choose **Key vaults.**

4. On the Key vaults section, choose **Create.**

5. On the **Basics** tab of **Create a key vault,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Enter **az-rg-1.**|
   |**Instance details**|
   |Key vault name|The vault name must contain only alphanumeric characters and dashes, and it cannot start with a number. *Example: az-securevault150*|
   |Region|Select **East US.**|
   |Pricing tier|Leave the default setting as Standard.|
   |Days to retain deleted vaults|Leave the default setting as 90.|

6. Select the **Review + create tab,** or select the blue Review + create button at the bottom of the page.
  
7. Select **Create.**

### Configure Key Vault firewall and virtual network settings.

1. In the Azure portal Search box, enter **key vaults.**

2. Browse to the key vault you previously created.

3. Select **Settings**, then **Networking**, and then the **Firewalls and virtual networks** tab.
   
4. Under Allow access from, select **Allow public access from specific virtual networks and IP addresses.**

5. Under the Virtual networks section, select + **Add a virtual network**, then select + **Add existing virtual networks.**

6. In the **Add networks** template, select your previously created virtual network from the **Virtual networks** dropdown list, and **Subnets** dropdown list.

7. At the bottom of the **Add networks** template, select **Enable**, then select **Add**. 

8. At the bottom of the **Firewalls and virtual networks** page, select **Apply.**

  > **Results**: You have created a key vault and configured key vault firewall and virtual network settings in the Azure portal.
