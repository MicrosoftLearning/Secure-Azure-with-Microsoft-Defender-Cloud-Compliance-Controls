---
lab:
    title: 'Exercise 01 - Create a virtual network infrastructure'
    module: 'Module 01 - Filter network traffic with a network security group using the Azure portal'
---

You can use a network security group to filter inbound and outbound network traffic to and from Azure resources in an Azure virtual network. Network security groups contain security rules that filter network traffic by IP address, port, and protocol. When a network security group is associated with a subnet, security rules are applied to resources deployed in that subnet.

## Architecture diagram

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/1bfec315-129b-48a9-9c35-1f21c837068f)

---

## Skilling tasks

- Create a network security group and security rules.
  
- Create application security groups.
  
- Create a virtual network and associate a network security group to a subnet.
  
- Deploy virtual machines and associate their network interfaces to the application security groups.
  
- Test traffic filters.

## Exercise instructions 

### Create a resource group and virtual network.

>**Note**: The following task creates a virtual network with a resource subnet.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)             
   
2. From the Azure portal menu, select + **Create a resource** > **Networking** > **Virtual network,** or search for Virtual Network in the portal search box.

3. Select **Create.**

4. On the **Basics** tab of **Create virtual network,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **Create new.** Enter **azure-rg-1.** Select **OK**|
   |**Instance details**|
   |Virtual network name|Enter **vnet-1.**|
   |Region|Select **East US 2.**|  
    
5. Select **Next: IP Addresses** at the bottom of the page.

6. In the **IP Addresses** tab, in **IPv4 address space,** select the garbage deletion icon to remove any address space that already appears, and then enter **10.0.0.0/16.**

7. Select **+ Add subnet.**

8. Enter or select the following information in **Add subnet:**

  ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/a9938432-5531-4f61-8d90-d8fb34823d8e)

9. Select **Add.**

10. Select **Review + create** at the bottom of the screen, and when validation passes, select **Create.**

### Create application security groups to enable you to group together servers with similar functions, such as web servers.

>**Note**: An application security group (ASGs) enables you to group together servers with similar functions, such as web servers.

1. From the Azure portal menu, select + **Create a resource** > **Networking** > **Application security group,** or search for Application security group in the portal search box.
   
2. Select **Create.**

3. On the **Basics** tab of **Create an application security group,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **azure-rg-1.**|
   |**Instance details**|
   |Name|Enter **asg-web.**|
   |Region|Select **East US.**|  
    
4. Select **Review + create.**

5. Select **Create.**

8. Repeat the previous steps, specifying the following values:
    
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **azure-rg-1.**|
   |**Instance details**|
   |Name|Enter **asg-mgmt.**|
   |Region|Select **East US.**|

4. Select **Review + create.**

5. Select **Create.**

### Create a network security groug to secure network traffic in your virtual network.

>**Note**: A network security group (NSG) secures network traffic in your virtual network.

1. From the Azure portal menu, select + **Create a resource** > **Networking** > **Network security group,** or use the portal search box to search for **Network security group** (not Network security group (classic).
   
2. Select **Create.**

3. On the **Basics** tab of **Create network security group,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **azure-rg-1.**|
   |**Instance details**|
   |Name|Enter **nsg-1.**|
   |Region|Select **East US.**|  
    
4. Select the **Review + create** tab, or select the blue **Review + create** button at the bottom of the page.

5. Select **Create.**

### Associate network security group to subnet

>**Note**: In this task, you associate the network security group with the subnet of the virtual network you created earlier.

1. In the search box at the top of the portal, enter **Network security group**. Select **Network security groups** in the search results.
   
2. Select **nsg-1.**

3. Select **Subnets** from the **Settings** section of **nsg-1.**

4. In the **Subnets** page, select + **Associate:**

   ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/3dd68bba-67f9-474f-8b94-98082bdec0b8)

5. Under **Associate subnet,** select **vnet-1 (azure-rg-1)** for **Virtual network.**

6. Select **subnet-1** for **Subnet,** and then select **OK.**

### Create security rules for the network security group with the subnet of the virtual network you created earlier.

1. Select **Inbound security rules** from the **Settings** section of **nsg-1.**
   
2. In **Inbound security rules** page, select + **Add:**

3. Create a security rule that allows ports 80 and 443 to the **asg-web** application security group. In **Add inbound security rule** page, enter or select this information:

   |Setting|Value|
   |---|---|
   |Source|Leave the default of **Any.**|
   |Source port ranges|Leave the default of **(*).**|
   |Destination|Select **Application security group.**|
   |Destination application security groups|Select **asg-web.**|
   |Service|Leave the default of **Custom.**|
   |Destination port ranges|Enter **80,443.**|
   |Protocol|Select **TCP.**|
   |Action|Leave the default of **Allow.**|
   |Priority|Leave the default of **100.**|
   |Name|Enter **allow-web-all.**|

4. Select **Add.**

5. Complete previuos steps with the following information:

   |Setting|Value|
   |---|---|
   |Source|Leave the default of **Any.**|
   |Source port ranges|Leave the default of **(*).**|
   |Destination|Select **Application security group.**|
   |Destination application security group|Select **asg-mgmt.**|
   |Service|Select **RDP.**|
   |Action|Leave the default of **Allow.**|
   |Priority|Leave the default of **110.**|
   |Name|Enter *allow-rdp-all.*|
   
6. Select **Add.**

### Create two virtual machines (VMs) in the virtual network you created earlier.

1. From the Azure portal menu, select + **Create a resource** > **Compute** > **Virtual machine,** or search for Virtual machine in the portal search box.
   
2. In **Create a virtual machine,** enter or select this information in the **Basics** tab:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Susbcription|Select your subscription|
   |Resource group|Select **azure-rg-1.**|
   |**Instance details**|
   |Virtual machine name|Enter **vm-1.**|
   |Region|Select **(US) East US.**|
   |Availability options|Leave the default of **No infrastructure redundancy required.**|
   |Security type|Leave the default of **Standard.**|
   |Image|Select **Windows Server 2022 Datacenter - x64 Gen2.**|
   |VM architecture|Select **x64.**|
   |Run with Azure Spot discount|Leave the default of unchecked|
   |Size|Leave the default of **Standard_D2s_v3-2 vcpus, 8 GiB memory.**|
   |**Administrator account**|
   |Authentication type|Select **Password.**|
   |Username|Enter **Tenantadmin1.**|
   |Password|Enter **Superuser#150.**|
   |Confirm password|Reenter **Superuser#150.**|
   |**Inbound port rules**|
   |Select inbound ports|Select **None.**|

4. Select the **Networking** tab.

5. In the **Networking** tab, enter or select the following information:

   |Setting|Value|
   |---|---|
   |**Network interface**|
   |Virtual network|Select **vnet-1.**|
   |Subnet|Select **default (10.0.0.0/24).**|
   |Public IP|Leave the default of a new public IP.|
   |NIC network security group|Select **None.**|
   
6. Select the **Review + create** tab, or select the blue **Review + create** button at the bottom of the page.

7. Select **Create.** The VM may take a few minutes to deploy.
  
   - Create the second virtual machine

   - Repeat the previous steps to create a second virtual machine named **vm-2.**

   - Wait for the VMs to complete deployment before advancing to the next section.

### Associate network interfaces to an application security group

>**Note**: When you created the VMs, Azure created a network interface for each VM, and attached it to the VM. Add the network interface of each VM to one of the application security groups you created previously:

1. In the search box at the top of the portal, enter **Virtual machine.** Select **Virtual machines** in the search results.

2. Select **vm-1.**
 
3. Select **Networking** from the **Settings** section of **vm-1.**

4. Select the **Application security groups** tab, then select **Configure the application security groups.**

   ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/724130e0-6081-40ad-9864-16e28ad941d0)

5. In **Configure the application security groups,** select **asg-web.** in the **Application security groups** pull-down menu, then select **Save.**

6. Repeat previous steps for **vm-2**, selecting **asg-mgmt** in the **Application security groups** pull-down menu.

### Test traffic filters

1. In the search box at the top of the portal, enter **Virtual machine.** Select **Virtual machines** in the search results.
  
2. Select **vm-2.**
   
3. On the **Overview** page, select the **Connect** button and then select **Native RDP.**

4. Select **Download RDP file.**

5. Open the downloaded rdp file and select **Connect.** Enter the username and password you specified when creating the VM.

6. Select **OK.**

7. You may receive a certificate warning during the connection process. If you receive the warning, select **Yes** or **Continue,** to continue with the connection.

   The connection succeeds, because inbound traffic from the internet to the **asg-mgmt** application security group is allowed through port 3389.

   The network interface for **vm-2** is associated with the **asg-mgmt** application security group and allows the connection.

8. Open a PowerShell session on **vm-2.** Connect to **vm-1** using the following:

    ```powershell
    mstsc /v:vm-1
    ```
    
   The RDP connection from **vm-2** to **vm-1** succeeds because virtual machines in the same network can communicate with each other over any port by default.

   You can't create an RDP connection to the **vm-1** virtual machine from the internet. The security rule for the **asg-web** prevents connections to port 3389 inbound from the internet.
   Inbound traffic from the Internet is denied to all resources by default.

9. To install Microsoft Internet Information Services (IIS) on the **vm-1** virtual machine, enter the following command from a PowerShell session on the **vm-1** virtual machine:

      ```powershell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
10. After the IIS installation is complete, disconnect from the **vm-1** virtual machine, which leaves you in the **vm-2** virtual machine remote desktop connection.

11. Disconnect from the **vm-2** VM.

12. Search for **vm-1** in the portal search box.
    
13. On the **Overview** page of **vm-1**, note the **Public IP address** for your VM. The address shown in the following example is 20.230.55.178, your address is different:

    ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/c32ef7df-306a-4b01-942d-da7325d8f10a)

14. To confirm that you can access the **vm-1** web server from the internet, open an internet browser on your computer and browse to `http://public-ip-address-from-previous-step>`.

    You see the IIS default page, because inbound traffic from the internet to the **asg-web** application security group is allowed through port 80.

    The network interface attached for **vm-1** is associated with the **asg-web** application security group and allows the connection.

> **Results**: You have created a created a virtual network infrastructure and filtered network traffic with a network security group using the Azure portal.

> **Note**: Do not remove the resources from this lab as they are needed for Exercise 05a - Configure Key Vault firewall and virtual networks.
