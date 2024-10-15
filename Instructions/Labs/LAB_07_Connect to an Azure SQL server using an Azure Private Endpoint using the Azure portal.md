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
   
2. From the Azure portal menu, select + **Create a resource** > **Networking** > **Virtual network,** or search for Virtual Network in the portal search box.

3. Select **Create.**

4. On the **Basics** tab of **Create virtual network,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Enter **az-rg-1.**|
   |**Instance details**|
   |Virtual network name|Enter **myVNet1a.**|
   |Region|Select **(US) East US.**|  
    
5. Select **Next** to proceed to the **Security** tab.
  
6. Select **Enable Azure Bastion** in the Azure Bastion section of the Security tab.

   >**Note**: Azure Bastion is a paid service that provides secure RDP/SSH connectivity to your virtual machines over TLS. When you connect via Azure Bastion, your virtual machines do not need a public IP address. 

7. Enter or select the following information in the **Azure Bastion** field:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Azure Bastion host |Enter **mybastionhost1a.**|
   |Azure Bastion public IP address name|Select **Create a public IP address**|

9. Select **Next** to proceed to the **IP addresses** tab.

10. In the enabled **IPv4 Address space** box under the **Subnets** column, click the **default** entry.

11. In **Edit subnet** template, enter or select the following information:

    |Setting|Value|
    |---|---|
    |**Project details**|
    |Subnet purpose|Leave the default of **Default.**|
    |Name|**mysubnet1a**|
    |IPv4 address range|Leave the default of **10.0.0.0/16**|
    |Starting address|Leave the default of **/24 (256 addresses)**|

13. At the bottom of the **Edit subnet** page, select **Save.**

14. At the bottom of the **IP addresses** page, select **Review + create.**

    >**Note**: Bastion deployment may take up to 15 minutes for complete instantiation.

15. At the bottom of the **Review + create** page, select **Create.**
 
### Create a virtual machine.

>**Note**: In this task, you'll create a virtual machine that will be used to test the private endpoint.

1. In the portal, search for and select virtual machines.

2. In **Virtual machines,** select **+ Create,** then **Azure virtual machine.**

3. In Create a virtual machine, enter or select this information in the Basics tab:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Susbcription|Select your subscription|
   |Resource group|Select **az-rg-1.**|
   |**Instance details**|
   |Virtual machine name|Enter **myVM.**|
   |Region|Select **(US) East US.**|
   |Availability options|From the Availability Zone drop-down menu, select **No infrastructure redundancy required.**|
   |Security type|From the Security type drop-down menu, select **Standard.**|
   |Image|Select **Windows Server 2022 Datacenter - x64 Gen2.**|
   |VM architecture|Select **x64.**|
   |Run with Azure Spot discount|Leave the default of unchecked|
   |Size|Leave the default of **Standard_D2s_v3-2 vcpus, 8 GiB memory.**|
   |**Administrator account**|
   |Authentication type|Select **Password.**|
   |Username|Enter **Tenantadmin2.**|
   |Password|Enter **Superuser#170.**|
   |Confirm password|Reenter **Superuser#170.**|
   |**Inbound port rules**|
   |Select inbound ports|Select **None.**|

5. Select the **Networking** tab, or select **Next: Disks,** then **Next: Networking.**
  
6. In the **Networking** tab, enter or select this information:

   |Setting|Value|
   |---|---|
   |**Network interface**|
   |Virtual network|Select **myVNet1a.**|
   |Subnet|Select **mySubnet1a.**|
   |Public IP|Select **None.**|
   |NIC network security group|Select **Basic.**|
   |Public inbound ports|Select **None.**|
  
6. Select **Review + create.**

7. Review the settings, and then select **Create.**

### Create an Azure SQL server and private endpoint

>**Note**: In this task, you'll create a SQL server in Azure.

1. From the Azure portal menu, select + **Create a resource** > **Databases** > **SQL database.**
   
2. In the **Basics** tab of **Create SQL database,** enter or select this information:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **CreateSQLEndpointTutorial.**|
   |**Database details**|
   |Database name|Enter **mysqldatabase.**|
   |Server|Select **Create new.**|  

3. In **Create SQL Database Server,** enter or select this information:
  
   |Setting|Value|
   |---|---|
   |**Server details**|
   |Server name|Enter **mysqlserver1a.** If this name is taken, create a unique name.|
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
   |Want to use SQL elastic pool|Select **No.**|
   |Compute + Storage|Take default settings or select **Configure database** to configure compute and storage settings.|
   |**Backup storage redundancy**|
   |Backup storage redundancy|Select **Locally-redundant backup storage.**|
   
5. Select the **Networking** tab or select the **Next: Networking** button.

6. In the **Networking** tab, enter or select this information:

   |Setting|Value|
   |---|---|
   |**Network connnectivity**|
   |Connectivity method|Select **Private endpoint.**|

7. Select + **Add private endpoint** in **Private endpoints.**

8. In **Create private endpoint,** enter or select this information:

   |Setting|Value|
   |---|---|
   |Subscription|Select your subscription.|
   |Resource group|Select **CreateSQLEndpointTutorial.**|
   |Location|Select **East US.**|
   |Name|Enter **myPrivateSQLendpoint.**|
   |Target sub-resource|Leave the default Default **SqlServer.**|
   |**Networking**|
   |Virtual network|Select **myVNet1a.**|
   |Subnet|Select **mySubnet1a.**|
   |**Private DNS integration**|
   |Intergrate with private DNS zone|Leave the default **Yes.**|
   |Private DNS Zone|Leave the default **(New) privatelink.database.windows.net.**|

9. Select **OK.**

10. Select **Review + create.**

11. Select **Create.**

### Disable public access to Azure SQL logical server

>**Note**: For this task, assume you would like to disable all public access to your Azure SQL server, and only allow connections from your virtual network.

1. In the Azure portal search box, enter **mysqlserver** or the server name you entered in the previous steps.

2. On the **Networking** page, select **Public access** tab, then select **Disable** for **Public network access.**

   ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/44ff5c24-70cf-49ed-b2ab-5e210c478b3a)


4. Select **Save.**

### Test connectivity to private endpoint

>**Note**: In this task, you'll use the virtual machine you created in the previous steps to connect to the SQL server across the private endpoint.

1. Select **Resource groups** in the left-hand navigation pane.

2. Select **CreateSQLEndpointTutorial.**

3. Select **myVM.**

4. On the overview page for **myVM,** select Connect then **Bastion.**

5. Enter the username **Tenantadmin2** and password **Superuser#170** that you entered during the virtual machine creation.

   **Important:** Go to the Edge settings/Pop-ups and redirects/and switch the Blocked switch to **off,** before selecting Connect.

7. Select **Connect** button.
  
8. Open Windows PowerShell on the server after you connect.

9. Enter `nslookup sqlserver-name.database.windows.net.` Replace **sqlserver-name** with the name of the SQL server you created in the previous steps. You'll receive a message similar to what is displayed below:

   ````  
   Server:  UnKnown
   Address:  168.63.129.16
   
   Non-authoritative answer:
   Name:    mysqlserver1a.privatelink.database.windows.net
   Address:  10.1.0.5
   Aliases:  mysqlserver1a.database.windows.net
   ````
    
>**Note**: A  private IP address of 10.1.0.5 is returned for the SQL server name. This address is in **mySubnet1a** subnet of **myVNet1a** virtual network you created previously.

9. Install [SQL Server Management Studio](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?preserve-view=true&view=sql-server-2017) on **myVM.**
 
10. Open **SQL Server Management Studio.**

11. In **Connect to server,** enter or select this information:

    |Setting|Value|
    |---|---|
    |Server type|Select **Database Engine.**|
    |Server name|Enter **sqlserver1a.database.windows.net.**|
    |Authentication|Select **SQL Server Authentication.**|
    |User name|Enter **Tenantadmin2**.|
    |Password|Enter **Superuser#170**.|
    |Remember password|Select **Yes.**|
   
12. Select **Connect.**

13. Browse databases from left menu.

14. (Optionally) Create or query information from mysqldatabase.

15. Close the remote desktop connection to myVM.
  
> **Results**: You have connected to an Azure SQL server using an Azure Private Endpoint using the Azure portal.
