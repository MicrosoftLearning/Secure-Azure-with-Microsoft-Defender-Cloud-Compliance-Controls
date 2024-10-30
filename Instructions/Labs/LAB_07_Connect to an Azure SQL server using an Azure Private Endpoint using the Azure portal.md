---
lab:
    title: 'Exercise 07 - Connect to an Azure SQL server using an Azure Private Endpoint using the Azure portal'
    module: 'Module 08 - Connect to an Azure SQL server using an Azure Private Endpoint using the Azure portal'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


Azure Private endpoint is the fundamental building block for Private Link in Azure. It enables Azure resources, like virtual machines (VMs), to privately and securely communicate with Private Link resources such as Azure SQL server.

---

## Skilling tasks

- Create a virtual network and bastion host.
  
- Create a virtual machine.
  
- Create an Azure SQL server and private endpoint.
  
- Test connectivity to the SQL server private endpoint.

## Exercise instructions 

### Create a resource group and virtual network.

>**Note**: The bastion host will be used to connect securely to the virtual machine for testing the private endpoint. 

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. In the search box at the top of the portal, type **Virtual networks.** Select **Virtual networks** in the search results.

3. On the **Virtual networks** page, select **+ Create.**

4. On the **Basics** tab of **Create virtual network**, enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |**Instance details**|
   |Virtual network name|Enter **vnet-2.**|
   |Region|Select **(US) East US.**|  
    
5. Select **Next** to proceed to the **Security** tab.
  
6. Select **Enable Azure Bastion** in the Azure Bastion section of the Security tab.

   >**Note**: Azure Bastion is a paid service that provides secure RDP/SSH connectivity to your virtual machines over TLS. When you connect via Azure Bastion, your virtual machines do not need a public IP address. 

7. Enter or select the following information in the **Azure Bastion** field:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Azure Bastion host |Enter **az-bastionhost-1a.**|
   |Azure Bastion public IP address name|Select **Create a public IP address**|
   |Add a public IP address|Select **OK**|

9. Select **Next** to proceed to the **IP addresses** tab.

10. In the existing configured **IPv4 address space** box under the **Subnets** column, click the **default** entry.

11. In **Edit subnet** template, enter or select the following information:

    |Setting|Value|
    |---|---|
    |**Project details**|
    |Subnet purpose|Leave the default setting as Default.|
    |Name|**subnet-2**|
    |Include an IPv4 address space|Leave the default setting with the Checkmark.|
    |IPv4 address range|Leave the default setting as 10.0.0.0/16.|
    |Starting address|10.0.0.0.|
    |Size|Leave the default setting as /24 (256 addresses).|
    |Subnet address range|10.0.0.0-10.0.0.255.|

13. At the bottom of the **Edit subnet** page, select **Save.**

14. At the bottom of the **IP addresses** page, select **Review + create.**

    >**Note**: Bastion deployment may take up to 15 minutes for complete instantiation.

15. At the bottom of the **Review + create** page, select **Create.**
 
### Create a virtual machine.

>**Note**: In this task, you'll create a virtual machine that will be used to test the private endpoint.

1. In the portal, search for and select **Virtual machines.**

2. In **Virtual machines,** select **+ Create**, then **Azure virtual machine.**

3. In Create a virtual machine, enter or select this information in the **Basics** page:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Susbcription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |**Instance details**|
   |Virtual machine name|Enter **vm-3.**|
   |Region|Select **(US) East US.**|
   |Availability options|From the Availability Zone drop-down menu, select **No infrastructure redundancy required.**|
   |Security type|From the Security type drop-down menu, select **Standard.**|
   |Image|Select **Windows Server 2022 Datacenter - x64 Gen2.**|
   |VM architecture|Select **x64.**|
   |Run with Azure Spot discount|Leave the default setting as unchecked.|
   |Size|Leave the default setting as Standard_D2s_v3-2 vcpus, 8 GiB memory.|
   |**Administrator account**|
   |Username|Enter **Tenantadmin2.**|
   |Password|Enter **Superuser#170.**|
   |Confirm password|Reenter **Superuser#170.**|
   |**Inbound port rules**|
   |Select inbound ports|Select **None.**|

5. Select **Next: Disks,** then **Next: Networking.**
  
6. In the **Networking** page, enter or select this information:

   |Setting|Value|
   |---|---|
   |**Network interface**|
   |Virtual network|Select **vnet-2.**|
   |Subnet|Select **subnet-2 (10.0.0.0/24).**|
   |Public IP|Select **None.**|
   |NIC network security group|Select **Basic.**|
   |Public inbound ports|Select **None.**|
   |Select inbound ports|Leave the default setting as blank.|
   |Delete NIC when VM is deleted|Leave the default setting as Enable accelerated networking checked.|
   |Load balancing|Leave the default setting as None.|
  
6. Select **Review + create.**

7. Review the settings, and then select **Create.**

### Create an Azure SQL server and private endpoint

>**Note**: In this task, you'll create a SQL server in Azure.

1. In the search box at the top of the portal, enter **sql database.** Select **SQL databases** in the search results.

2. On the **SQL databases** page, select **+ Create.**
   
3. In the **Basics** tab of **Create SQL database**, enter or select this information:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |**Database details**|
   |Database name|Enter **az-sql-db1a.**|
   |Server name|Enter **az-sql-svr1a.** If this name is taken, create a unique name.|
   |Location|Select **(US) East US.**|
   |**Authentication**|
   |Authentication method|Select **Use SQL authentication.**|
   |Server admin login|Enter **Tenantadmin2.**|
   |Password|Enter **Superuser#170.**|
   |Confirm passowrd|Enter **Superuser#170.**|

4. Select **OK.**
   
   |Setting|Value|
   |---|---|
   |**Database details**|
   |Want to use SQL elastic pool|Leave the default setting as No.|
   |Workload environment|Leave the default setting as Development.|
   |Compute + Storage|Leave the default setting as General Purpose - Serverless.|
   |**Backup storage redundancy**|
   |Backup storage redundancy|Select **Locally-redundant backup storage.**|
   
5. Select the **Networking** tab or select the **Next: Networking** button.

6. In the **Networking** tab, enter or select this information:

   |Setting|Value|
   |---|---|
   |**Network connnectivity**|
   |Connectivity method|Select **Private endpoint.**|
   |Connection policy|Leave the default setting as Default - Uses Redirect policy for all client connections originating inside of Azure (except Private Endpoint connections) and Proxy for all client connections originating outside Azure|
   |Encryption connections|Leave the default setting as TLS.12|

7. Select + **Add private endpoint** in **Private endpoints.**

8. In **Create private endpoint**, enter or select this information:

   |Setting|Value|
   |---|---|
   |Subscription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |Location|Select **East US.**|
   |Name|Enter **az-pe-1a.**|
   |Target sub-resource|Leave the default setting as SqlServer.|
   |**Networking**|
   |Virtual network|Select **vnet-2.**|
   |Subnet|Select **subnet-2.**|
   |**Private DNS integration**|
   |Intergrate with private DNS zone|Leave the default setting as Yes.|
   |Private DNS Zone|Leave the default setting as (New) privatelink.database.windows.net.|

9. Select **OK.**

10. Select **Review + create.**

11. Select **Create.**

### Disable public access to Azure SQL logical server

>**Note**: For this task, assume you would like to disable all public access to your Azure SQL server, and only allow connections from your virtual network. The **Public access** setting may default to **Disable.**

1. In the Azure portal search box, enter **az-sql-svr1a** or the server name you entered in the previous steps.

2. Select **Networking** from the **Security** section of **az-sql-svr1a.** On the **Networking** page, select **Public access** tab, then select **Disable** for **Public network access.**

   ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/44ff5c24-70cf-49ed-b2ab-5e210c478b3a)

3. Select **Save.**

### Test connectivity to private endpoint

>**Note**: In this task, you'll use the virtual machine you created in the previous steps to connect to the SQL server across the private endpoint.

1. Select **Resource groups** in the left-hand navigation pane.

2. Select **az-rg-1.**

3. Select **vm-3.**

4. On the overview page for **vm-3**, select Connect then **Bastion.**

5. Enter the username **Tenantadmin2** and password **Superuser#170** that you entered during the virtual machine creation.

   **Important:** Go to the Edge settings/Pop-ups and redirects/and switch the Blocked switch to **off,** before selecting Connect.

7. Select **Connect** button.
  
8. Open Windows PowerShell on the server after you connect.

9. Enter `nslookup sqlserver-name.database.windows.net.` Replace **sqlserver-name** with the name of the SQL server you created in the previous steps. You'll receive a message similar to what is displayed below:

   ````  
   Server:  UnKnown
   Address:  168.63.129.16
   
   Non-authoritative answer:
   Name:    az-sql-svr1a.privatelink.database.windows.net
   Address:  10.1.0.5
   Aliases:  az-sql-svr1a.database.windows.net
   ````
    
>**Note**: A  private IP address of 10.1.0.5 is returned for the SQL server name. This address is in **az-sql-svr1a** subnet of **vnet-2** virtual network you created previously.

9. Install [SQL Server Management Studio](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?preserve-view=true&view=sql-server-2017) on **vm-3.**
 
10. Open **SQL Server Management Studio.**

11. In **Connect to server,** enter or select this information:

    |Setting|Value|
    |---|---|
    |Server type|Select **Database Engine.**|
    |Server name|Enter **az-sql-svr1a.database.windows.net.**|
    |Authentication|Select **SQL Server Authentication.**|
    |User name|Enter **Tenantadmin2**.|
    |Password|Enter **Superuser#170**.|
    |Remember password|Select **Yes.**|
    |Connectivity Security|
    |Encryption|Leave the default setting as Mandatory.|
   
13. Select **Connect.**

14. Browse databases from left menu.

15. Close the remote desktop connection to vm-3.
  
> **Results**: You have connected to an Azure SQL server using an Azure Private Endpoint using the Azure portal.
