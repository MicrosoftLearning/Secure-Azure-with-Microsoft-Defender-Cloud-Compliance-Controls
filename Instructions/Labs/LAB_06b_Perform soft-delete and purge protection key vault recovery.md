---
lab:
    title: 'Exercise 06b - Perform soft-delete and purge protection key vault recovery'    
    module: 'Module 07 - Configure Azure Key Vault networking settings'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


You can use purge protection to prevent the deletion of your key vault, keys, secrets, and certificates by a malicious insider. Think of this as a recycle bin with a time based lock. You can recover items at any point during the configurable retention period. You will not be able to permanently delete or purge a key vault until the retention period elapses. Once the retention period elapses the key vault or key vault object will be purged automatically.

---

## Skilling tasks

- Verify if soft delete is enabled on a key vault and enable soft delete.

- List, recover, or purge a soft-deleted key vault.

- List, recover or purge soft deleted secrets, keys, and certificates.

## Exercise instructions 

### Verify if soft delete is enabled on a key vault and enable soft delete

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. Select your key vault.

3. Within the **Essentials** field, verify that **Soft-delete** is set to **Enable.**

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/06131a60-7f00-4764-a424-87ea41a78394)


### List, recover, or purge a soft-deleted key vault.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. Click on the search bar at the top of the page.

3. Search for the **Key Vault** service. Do not click an individual key vault.

4. At the top of the screen click the option to "Manage deleted vaults"

5. A context pane will open on the right side of your screen.

6. Select your subscription.

7. If your key vault has been soft deleted it will appear in the context pane on the right.

8. If there are too many vaults, you can either click "Load More" at the bottom of the context pane or use CLI or PowerShell to get the results.

9. Once you find the vault you wish to **recover** or **purge,** select the **checkbox** next to it.

10. Select the recover option at the bottom of the context pane if you would like to recover the key vault.

11. Select the purge option if you would like to permanently delete the key vault.

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/f41c0673-3832-4d3f-8b05-48e46e6c2282)


### List, recover, or purge soft-deleted secrets, keys, and certificates.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. Select your key vault.

3. Select the blade corresponding to the secret type you want to manage (keys, secrets, or certificates).

4. At the top of the screen, click on "Manage deleted (keys, secrets, or certificates)

5. A context pane will appear on the right side of your screen.

6. If your secret, key, or certificate does not appear in the list, it is not in the soft-deleted state.

7. Select the secret, key, or certificate you would like to manage.

8. Select the option to recover or purge at the bottom of the context pane.

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/dab95f78-1642-4883-b56f-70e1e5320d45)


  > **Results**: You have performed Azure key Vault recovery management with soft delte and purge protection in the Azure portal.
