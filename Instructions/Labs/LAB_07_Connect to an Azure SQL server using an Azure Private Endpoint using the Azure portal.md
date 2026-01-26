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

### Estimated Lab Duration: 20 minutes

## Exercise instructions 

### Create a resource group and virtual network.

>**Note**: The bastion host will be used to connect securely to the virtual machine for testing the private endpoint. 

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. In the search box at the top of the portal, type **virtual networks.** Select **Virtual networks** in the search results.

3. On the **Virtual networks** page, select **+ Create.**

4. On the **Basics** tab of **Create virtual network**, enter or select this information:
   
   |Setting|Value|
   |---|---|
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
   |Azure Bastion host |Enter **az-bastionhost-1a.**|
   |Azure Bastion public IP address name|Select **Create a public IP address**|
   |Add a public IP address|Select **OK**|

8. Select **Next** to proceed to the **IP addresses** tab.

9. In the existing configured **IPv4 address space** box under the **Subnets** column, click the **default** entry.

10. In **Edit subnet** template, enter or select the following information:

    |Setting|Value|
    |---|---|
    |Subnet purpose|Leave the default setting as Default.|
    |Name|**subnet-2**|
    |Include an IPv4 address space|Leave the default setting with the checkmark.|
    |IPv4 address range|Leave the default setting as 10.0.0.0/16.|
    |Starting address|10.0.0.0.|
    |Size|Leave the default setting as /24 (256 addresses).|
    |Subnet address range|10.0.0.0-10.0.0.255.|

11. At the bottom of the **Edit subnet** page, select **Save.**

12. At the bottom of the **IP addresses** page, select **Review + create.**

13. At the bottom of the **Review + create** page, select **Create.**

>**Note**: Bastion deployment may take up to 15 minutes for complete instantiation.
 
### Create a virtual machine.

>**Note**: In this task, you'll create a virtual machine that will be used to test the private endpoint.

1. In the portal, search for and select **virtual machines.**

2. In **Virtual machines,** select **+ Create**, then **Azure virtual machine.**

3. In Create a virtual machine, enter or select this information in the **Basics** page:

   |Setting|Value|
   |---|---|
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
   |Public inbound ports|Select **None.**|
   |Select inbound ports|The default setting is greyed out.|

4. Select **Next: Disks,** then **Next: Networking.**
  
5. In the **Networking** page, enter or select this information:

   |Setting|Value|
   |---|---|
   |**Network interface**|
   |Virtual network|Select **vnet-2.**|
   |Subnet|Leave the default setting as subnet-2 (10.0.0.0/24).|
   |Public IP|Leave the default setting as (new) vm-3-ip.|
   |NIC network security group|Leave the default setting as None.|
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
   |Subscription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |**Database details**|
   |Database name|Enter **az-sql-db1a.**|
   |Server|Select **Create new.**|
   |**Server details**|
   |Server name|Enter **az-sql-srv1a.**|
   |Location|Leave the default setting as (US) East US|
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

7. In the **Private endpoints** section, select **+ Add private endpoint.**

8. Select **Review + create.**

9. Select **Create.**

10. In **Create private endpoint**, enter or select this information:

       |Setting|Value|
       |---|---|
       |Subscription|Select your subscription.|
       |Resource group|Select **az-rg-1.**|
       |Location|Select **East US.**|
       |Name|Enter **az-pe1a.**|
       |Target sub-resource|Leave the default setting as SqlServer.|
       |**Networking**|
       |Virtual network|Select **vnet-2.**|
       |Subnet|Select **subnet-2.**|
       |**Private DNS integration**|
       |Intergrate with private DNS zone|Leave the default setting as Yes.|
       |Private DNS Zone|Leave the default setting as (New) privatelink.database.windows.net.|

12. Select **OK.**

13. Select **Review + create.**

14. Select **Create.**

>**Note**: Azure SQL server and private endpoint deployment may take up to 10 minutes for complete instantiation.

### Allow certain public internet IP addresses to access your Azure SQL logical server

>**Note**: For this task, assume you want to enable public access to your Azure SQL server and allow connections only from your virtual network. The Public access setting may default to **Disabled.**

1. In the Azure portal search box, enter **az-sql-srv1a** or the server name you entered in the previous steps.
   
2. Select **Networking** from the **Security** section of **az-sql-srv1a.**
  
3. On the **Networking** page, go to the **Public access** tab.
  
4. Check if **Public network access** is disabled. If it is disabled, select **Selected networks** for Public network access.

>**Note**: Connections from the IP addresses configured in the Firewall rules section below will have access to this database. By default, no public IP addresses are allowed.

5. If required, go to the **Firewall rules** section on the **Networking** page, and select **+ Add your client IPv4 address** if your client IP address is not already populated in the **Rule name,** **Starting IPv4 address,** and **End IPv4 address** fields.

   ![image](https://github.com/user-attachments/assets/fff5bfb1-53fd-40ea-9a31-5a095e7f3dbc) 

7. Select **Save.**

### Test connectivity to private endpoint

>**Note**: In this task, you'll use the virtual machine you created in the previous steps to connect to the SQL server across the private endpoint.

1. In the Azure portal search box, type **vm-3,** and select it from the Resources drop-down list.

2. On the **Overview** page for vm-3, select **Connect,** and then choose **Bastion.**

3. Enter the username **Tenantadmin2** and password **Superuser#170** that you entered during the virtual machine creation.

   **Important:** Important: Go to Edge settings and navigate to **Pop-ups and redirects.** Select the radial option labeled **Always allow pop-ups and redirects from https://portal.azure.com,** and then click **Done.**

4. Select **Connect** button.
  
5. Open Windows PowerShell on the server after you connect.

6. To verify name resolution of the private endpoint, enter the following command in the terminal window:

   ```bash
   nslookup server-name.database.windows.net

>**Note**: Replace **sqlserver-name** with the name of the SQL server you created in the previous steps. For example, enter **nslookup az-sql-srv1a.database.windows.net** You’ll receive a message similar to the one shown below:

   ````
   
   Server:  UnKnown
   Address:  168.63.129.16
   
   Non-authoritative answer:
   Name:    az-sql-srv1a.privatelink.database.windows.net
   Address:  10.1.0.5
   Aliases:  az-sql-srv1a.database.windows.net
   ````
   
>**Note**: A  private IP address of 10.1.0.5 is returned for the SQL server name. This address is in **az-sql-srv1a** subnet of **vnet-2** virtual network you created previously.

7. Install [SQL Server Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?preserve-view=true&amp;view=sql-server-2017) on **vm-3.**
 
8. Open **SQL Server Management Studio.**

9. In **Connect to server,** enter or select this information:

    |Setting|Value|
    |---|---|
    |Server type|Leave the default setting as Database Engine.|
    |Server name|Enter **az-sql-srv1a.database.windows.net.**|
    |Authentication|Select **SQL Server Authentication.**|
    |User name|Enter **Tenantadmin2**.|
    |Password|Enter **Superuser#170**.|
    |Remember password|Select **Yes.**|
    |Connectivity Security|
    |Encryption|Leave the default setting as Mandatory.|
   
10. Select **Connect.**

11. Browse databases from left menu.

12. Close the remote desktop connection to vm-3.
  
> **Results**: You have connected to an Azure SQL server using an Azure Private Endpoint using the Azure portal.
