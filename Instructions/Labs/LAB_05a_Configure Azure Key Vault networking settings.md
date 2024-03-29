---
lab:
    title: 'Exercise 05a - Configure Key Vault firewall and virtual networks'    
    module: 'Module 05 - Configure Azure Key Vault networking settings'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


You can use the Azure portal to configure the Azure Key Vault networking settings to work with other applications and Azure services. 

---

## Skilling tasks

- Create a key vault using the Azure portal.

- Add an exsiting virtual network to a firewall and virtual network rules.

- Configure a virtual network and subnet to allow access to a key vault.

## Exercise instructions 

### Use the Azure portal to create an Azure Key Vault.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. In the Azure portal Search box, enter **Key Vault.**

3. From the results list, choose **Key Vault.**

4. On the Key vaults section, choose **Create.**

5. On the **Basics** tab of **Create a key vault,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Enter **az-rg-1.** Select **OK**|
   |**Instance details**|
   |Key vault name|Enter **AZAPLKeyVault.**|
   |Region|Select **East US**|
   |Pricing tier|System default **Standard**|
   |Days to retain deleted vaults|System default **90**|

7. Select the **Review + create tab,** or select the blue Review + create button at the bottom of the page.
  
8. Select **Create.**

### Configure Key Vault firewall and virtual network settings.

1. In the Azure portal Search box, enter **Key Vault.**

2. Browse to the key vault you previously created.

3. Select **Networking,** and then select the **Firewalls and virtual networks** tab.

4. Under Allow access from, select **Allow public access from specific virtual networks and IP addresses.**

5. Under the Virtual networks section, select + **Add a virtual network,** then select + **Add existing virtual networks.**

6. In the Add networks template, select your previously created virtual network from the **Virtual networks** dropdown list, and **Subnets** dropdown list.

7. At the bottom of the Add networks template, click **Add.**

  > **Results**: You have created a key vault and configured key vault firewall and virtual network settings in the Azure portal.
