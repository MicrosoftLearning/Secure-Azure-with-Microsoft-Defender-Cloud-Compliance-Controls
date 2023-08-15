---
lab:
    title: 'Exercise 05b - Configure Azure Key Vault recovery management with soft delete and purge protection'    
    module: 'Module 05 - Perform soft-delete and purge protection key vault recovery'
---

You can use purge protection to prevent the deletion of your key vault, keys, secrets, and certificates by a malicious insider. Think of this as a recycle bin with a time based lock. You can recover items at any point during the configurable retention period. You will not be able to permanently delete or purge a key vault until the retention period elapses. Once the retention period elapses the key vault or key vault object will be purged automatically.use the Azue portal to configure the Azure Key Vault networking settings to work with other applications and Azure services. 

---

## Skilling tasks

- Verify if soft delete is enabled on a key vault and enable soft delete.

- List, recover, or purge a soft-deleted key vault.

- List, recover or purge soft deleted secrets, keys, and certificates.

## Exercise instructions 

### Verify if soft delete is enabled on a key vault and enable soft delete

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. Select your key vault.

3. Click on the **Properties** blade.

4. Verify if the radio button next to soft-delete is set to **Enable purge protection.**

5. If soft-delete is not enabled on the key vault, click the radio button to enable soft delete and click **Save.**

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/07cb482e-aed2-451a-a62d-a33c03b198b0)


### List, recover, or purge a soft-deleted key vault.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. Click on the search bar at the top of the page.

3. Search for the "Key Vault" service. Do not click an individual key vault.

4. At the top of the screen click the option to "Manage deleted vaults"

5. A context pane will open on the right side of your screen.

6. Select your subscription.

7. If your key vault has been soft deleted it will appear in the context pane on the right.

8. If there are too many vaults, you can either click "Load More" at the bottom of the context pane or use CLI or PowerShell to get the results.

9. Once you find the vault you wish to **recover** or **purge,** select the **checkbox** next to it.

10. Select the recover option at the bottom of the context pane if you would like to recover the key vault.

11. Select the purge option if you would like to permanently delete the key vault.

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/b0602e3a-e243-487d-90e8-01f9084783bc)


### List, recover, or purge soft-deleted secrets, keys, and certificates.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. Select your key vault.

3. Select the blade corresponding to the secret type you want to manage (keys, secrets, or certificates).

4. At the top of the screen, click on "Manage deleted (keys, secrets, or certificates)

5. A context pane will appear on the right side of your screen.

6. If your secret, key, or certificate does not appear in the list, it is not in the soft-deleted state.

7. Select the secret, key, or certificate you would like to manage.

8. Select the option to recover or purge at the bottom of the context pane.

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/f10095de-5d70-4412-90cf-320a6eb935f9)

  > Results: You have performed Azure key Vault recovery management with soft delte and purge protection in the Azure portal.
