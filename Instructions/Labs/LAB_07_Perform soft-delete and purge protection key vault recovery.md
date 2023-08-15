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
   
2. Select your key vault.

3. Click on the **Properties** blade.

4. Verify if the radio button next to soft-delete is set to **Enable purge protection.**

5. If soft-delete is not enabled on the key vault, click the radio button to enable soft delete and click **Save.**

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/07cb482e-aed2-451a-a62d-a33c03b198b0)


### List, recover, or purge a soft-deleted key vault.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. Select your key vault.

3. Click on the **Properties** blade.

4. Verify if the radio button next to soft-delete is set to **Enable purge protection.**

5. If soft-delete is not enabled on the key vault, click the radio button to enable soft delete and click **Save.**

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/b0602e3a-e243-487d-90e8-01f9084783bc)


### List, recover, or purge soft-deleted secrets, keys, and certificates.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. Select your key vault.

3. Click on the **Properties** blade.

4. Verify if the radio button next to soft-delete is set to **Enable purge protection.**

5. If soft-delete is not enabled on the key vault, click the radio button to enable soft delete and click **Save.**

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/f10095de-5d70-4412-90cf-320a6eb935f9)

  > Results: You have performed Azure key Vault recovery management with soft delte and purge protection in the Azure portal.
