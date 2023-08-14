---
lab:
    title: 'Exercise 08 - Deploy a virtual machine to test connectivity privately and securely to the SQL server across the private endpoint'
    module: 'Module 08 - Connect to an Azure SQL server using an Azure Private Endpoint using the Azure portal'
---

Azure Private endpoint is the fundamental building block for Private Link in Azure. It enables Azure resources, like virtual machines (VMs), to privately and securely communicate with Private Link resources such as Azure SQL server.

---

## Skilling tasks

- Create a virtual network and bastion host.
  
- Create a virtual machine.
  
- Create an Azure SQL server and private endpoint.
  
- Test connectivity to the SQL server private endpoint.

## Exercise instructions 

### Create a resource group and virtual network.

    **Note:** The bastion host will be used to connect securely to the virtual machine for testing the private endpoint.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. From the Azure portal menu, select + **Create a resource** > **Networking** > **Virtual network,** or search for Virtual Network in the portal search box.

3. Select **Create.**

4. On the **Basics** tab of **Create virtual network,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **Create new.** Enter **CreateSQLEndpointTutorial.** Select **OK**|
   |**Instance details**|
   |Virtual network name|Enter *myVNet1a.*|
   |Region|Select **(US) East US.**|  
    
5. Select the **IP Addresses** tab or select the **Next: IP Addresses** button at the bottom of the page.

6. In the **IP Addresses** tab, enter this information:

   |Setting|Value|
   |---|---|
   |IPv4 address space|Enter **10.1.0.0/16.**|

7. Under **Subnet name,** select the word **default.**

8. In **Edit subnet,** enter this information:

   |Setting|Value|
   |---|---|
   |Subnet name|Enter **mySubnet1a.**|
   |Subnet address range|Enter **10.1.0.0/24.**|

9. Select **Save.**

10. Select the **Security** tab.

11. Under **Bastion host,** select **Enable.** Enter this information:
    |Setting|Value|
    |---|---|
    |Bastion name|Enter **myBastionHost.**|
    |AzureBstionSubnet address space|Enter **10.1.1.0/24.**|
    |Public IP Address|Select **Create new.** For **Name,** enter **My BastionIP.** Select **OK.**| 
 
### Create a virtual machine.

1. From the Azure portal menu, select + **Create a resource** > **Compute** > **Virtual machine** or search **Virtual Machine** in the portal search box.
   
2. In **Create a virtual machine,** enter or select the values in the **Basics** tab:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **CreateSQLEndpointTutorial.**|
   |**Instance details**|
   |Virtual network name|Enter *myVM.*|
   |Region|Select **(US) East US.**|  
   |Availability Options|Select **No infrastructure redundancy required.**|
   |Security type|Select **Standard.**|
   |Image|Select **Windows Server 2019 Datacenter - Gen2.Standard.**|
   |Azure Spot instance|Select **No.**|
   |Size|Choose VM size or take default setting.|
   |**Administrator account**|
   |Username|Enter a username.|
   |Password|Enter a Enter password.|
   |Confirm password|Reenter a password.|

3. Select the **Networking** tab, or select **Next: Disks,** then **Next: Networking.**
  
4. In the **Networking** tab, enter or select this information:

   |Setting|Value|
   |---|---|
   |**Network interface**|
   |Virtual network|Select **myVnet.**|
   |Subnet|Select **mySubnet.**|
   |Public IP|Select **None.**|
   |NIC network security group|Select **Basic.**|
   |Public inbound ports|Select **None.**|
  
5. Select **Review + create.**

6. Review the settings, and then select **Create.**

### Create an Azure SQL server and private endpoint

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
   |Server name|Enter **mysqlserver.** If this name is taken, create a unique name.|
   |Location|Select **(US) East US.**|
   |**Authentication**|
   |Authentication method|Select **Use SQL authentication.**|
   |Server admin login|Enter an administrator name of your choosing.|
   |Password|Enter an administrator name of your choosing. The password must be at least eight characters long and meet the defined requirements.|
   |Confirm passowrd|Reenter password.|

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
   |Target sub-resource|Select **SqlServer.**|
   |**Networking**|
   |Virtual network|Select **myVNet.**|
   |Subnet|Select **mySubnet.**|
   |**Private DNS integration**|
   |Intergrate with private DNS zone|Leave the default **Yes.**|
   |Private DNS Zone|Leave the default **(New) privatelink.database.windows.net.**|

 9. Select **OK.**

 10. Select **Review + create.**

 11. Select **Create.**

### Disable public access to Azure SQL logical server

    **Note:** For this task, assume you would like to disable all public access to your Azure SQL server, and only allow connections from your virtual network.

1. In the Azure portal search box, enter **mysqlserver** or the server name you entered in the previous steps.

2. On the **Networking** page, select **Public access** tab, then select **Disable** for **Public network access.**

3. Select **Save.**

### Test connectivity to private endpoint

1. Select **Resource groups** in the left-hand navigation pane.

2. Select **CreateSQLEndpointTutorial.**

3. Select **myVM.**

4. On the overview page for **myVM,** select Connect then **Bastion.**

5. Enter the username and password that you entered during the virtual machine creation.

6. Select **Connect** button.

7. Open Windows PowerShell on the server after you connect.

8. Enter nslookup <sqlserver-name>.database.windows.net. Replace <sqlserver-name> with the name of the SQL server you created in the previous steps. You'll receive a message similar to what is displayed below:

   |Setting|Value|
   |---|---|
   |**PowerShell**|
   |Server|UnKnown|
   |Address|168.63.129.16|
   |**Non-authoritative answer:**|
   |Name:|mysqlserver.privatelink.database.windows.net|
   |Address|10.1.0.5|
   |Alias|mysqlserver.database.windows.net|
 
    **Note:** A  private IP address of 10.1.0.5 is returned for the SQL server name. This address is in **mySubnet** subnet of **myVNet** virtual network you created previously.

9. Install *SQL Server Management Studio* on **myVM.**

10. Open **SQL Server Management Studio.**

11. In **Connect to server,** enter or select this information:

    |Setting|Value|
    |---|---|
    |Server type|Select **Database Engine.**|
    |Server name|Enter **<sqlserver-name>.database.windows.net.**|
    |Authentication|Select **SQL Server Authentication.**|
    |User name|Enter the username you entered during server creation.|
    |Password|Enter the password you entered during server creation.|
    |Remember password|Select **Yes.**|
   
12. Select **Connect.**

13. Browse databases from left menu.

14. (Optionally) Create or query information from mysqldatabase.

15. Close the remote desktop connection to myVM.
  
     > Results: You have connected to an Azure SQL server using an Azure Private Endpoint using the Azure portal.
