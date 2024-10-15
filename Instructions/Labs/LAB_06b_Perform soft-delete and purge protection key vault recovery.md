---
lab:
    title: 'Exercise 06b - Enable soft-delete in Azure key vault'    
    module: 'Module 07 - Configure Azure Key Vault networking settings'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


Deleting a key vault without soft delete enabled permanently deletes all secrets, keys, and certificates stored in the key vault. Accidental deletion of a key vault can lead to permanent data loss. Soft delete allows you to recover an accidentally deleted key vault for a configurable retention period.

---

## Skilling tasks

- Verify if soft delete is enabled on a key vault and enable soft delete.

## Exercise instructions 

### Verify if soft delete is enabled on a key vault and enable soft delete

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. Select your key vault.

3. From the **Settings blade,** select **Properties.**

4. Verify if the radio button next to soft-delete is set to **Enable purge protection (enforce a mandatory retention period for deleted vaults and vault objects).**

5. If soft-delete is not enabled on the key vault, click the **Enable purge protection (enforce a mandatory retention period for deleted vaults and vault objects)** radio button to enable soft delete and click **Save.**

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/06131a60-7f00-4764-a424-87ea41a78394)

> **Results**: You have performed Azure key Vault recovery management with soft delte and purge protection in the Azure portal.
