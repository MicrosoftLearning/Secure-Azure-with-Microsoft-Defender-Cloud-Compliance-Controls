---
lab:
    title: 'Exercise 07 - Configure Azure Key Vault recovery management with soft delete and purge protection'    
    module: 'Module 07 - Perform soft-delete and purge protection key vault recovery'
---

You can use purge protection to prevent the deletion of your key vault, keys, secrets, and certificates by a malicious insider. Think of this as a recycle bin with a time based lock. You can recover items at any point during the configurable retention period. You will not be able to permanently delete or purge a key vault until the retention period elapses. Once the retention period elapses the key vault or key vault object will be purged automatically.use the Azue portal to configure the Azure Key Vault networking settings to work with other applications and Azure services. 

---

## Skilling tasks

- Verify if soft delete is enabled on a key vault and enable soft delete.

- Grant access to a service principal to purge and recover deleted secrets.

- List, recover, or purge a soft-deleted key vault.

- List, recover or purge soft deleted secrets, keys, and certificates.

## Exercise instructions 

### Use the Azure portal to create an Azure Key Vault.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. In the Azure portal Search box, enter **Key Vault.**

3. From the results list, choose **Key Vault.**

4. On the Key vaults section, choose **Create.**

5. On the **Basics** tab of **Create a key vault,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Enter *myResourceGroup.* Select **OK**|
   |**Instance details**|
   |Key vault name|Enter *myAPLKeyVault.*|
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

5. Under the Virtual networks section, select + **Add existing virtual networks,** then select + **Add existing virtual networks.**

6. In the Add networks template, select your previously created virtual network from the **Virtual networks** dropdown list, and **Subnets** dropdown list.

7. At the bottom of the Add networks template, click **Add.**

  > Results: You have created a key vault and configured key vault firewall and virtual network settings in the Azure portal.
