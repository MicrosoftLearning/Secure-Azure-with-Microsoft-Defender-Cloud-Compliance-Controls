---
lab:
    title: 'Exercise 06b - Enable soft delete in Azure Key Vault'    
    module: 'Module 07 - Configure Azure Key Vault networking settings'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


Deleting a key vault without soft delete enabled permanently deletes all secrets, keys, and certificates stored in the key vault. Accidental deletion of a key vault can lead to permanent data loss. Soft delete allows you to recover an accidentally deleted key vault for a configurable retention period.

---

## Skilling tasks

- Verify if soft delete is enabled on a key vault and enable soft delete.

### Estimated Lab Duration: 5 minutes

## Exercise instructions 

### Verify if soft delete is enabled on a key vault and enable soft delete

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/).
  
2. In the search box at the top of the portal, enter **key vaults.** Select **Key vaults** in the search results.
   
3. Browse to the key vault you previously created.

4. From the **Settings** blade, select **Properties.**

5. Verify if the radio button next to soft-delete is set to **Enable purge protection (enforce a mandatory retention period for deleted vaults and vault objects).**

6. If soft-delete is not enabled on the key vault, click the **Enable purge protection (enforce a mandatory retention period for deleted vaults and vault objects)** radio button to enable soft delete and click **Save.**

   ![image](https://github.com/user-attachments/assets/8cc1d810-5a15-43fb-9dd8-1484af65897e)

> **Results**: You have successfully enabled soft delete, ensuring that deleted resources are retained for 90 days (by default) and can be recovered, effectively undoing the deletion through the Azure portal.
