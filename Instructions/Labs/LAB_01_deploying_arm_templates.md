---
lab:
    title: 'Lab: Create a virtual network infrastructure'
    module: 'Module 1: Filter network traffic with a network security group using the Azure portal'
---

# Lab: Create a virtual network infrastructure
# Student lab manual

## Lab scenario

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus lobortis, erat vel egestas faucibus, dui magna semper velit, id congue sapien lectus id turpis. Nam egestas tempus enim. Ut venenatis vehicula ex, id rutrum odio lacinia at. Donec congue, tortor sed fermentum imperdiet, mauris mi auctor dui, ac cursus ex augue a odio. Aliquam erat volutpat. Vivamus faucibus fringilla augue in dignissim. Quisque sit amet nulla id risus gravida auctor. Ut in est varius, cursus odio rhoncus, placerat erat. Suspendisse nec metus est.

## Objectives

After you complete this lab, you will be able to:

- Create a network security group and security rules
  
- Create application security groups
  
- Create a virtual network and associate a network security group to a subnet
  
- Deploy virtual machines and associate their network interfaces to the application security groups
  
- Test traffic filters

## Lab Setup

  - **Estimated Time**: 00 minutes

## Instructions

### Before you start

#### Setup Task

1. Integer dolor purus, gravida eu sem id, efficitur aliquet neque. 

1. Suspendisse viverra mauris in metus laoreet consectetur. 

1. Sed diam risus, convallis quis condimentum at, egestas malesuada libero. 

### Exercise 1: Create a resource group and virtual network.

#### Task 1: Use the Azure portal to create a resource group and virtual network

In this task, you will create a resource group and virtual network

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. From the Azure portal menu, select + **Create a resource** > **Networking** > **Virtual network,** or search for Virtual Network in the portal search box.

3. Select **Create.**

4. On the **Basics** tab of **Create virtual network,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **Create new.** Enter myResourceGroup. Select **OK**|
   |**Instance details**|
   |Virtual network name|Enter myVNet.|
   |Region|Select **(US) East US.**|  
    
5. Select the **Review + create** tab, or select the blue Review + create button at the bottom of the page.

6. Select **Create.**

### Exercise 2: Create application security groups.

#### Task 2: Use the Azure portal to create a resource group and virtual network

In this task, you will create application security group (ASGs) that enable you to group together servers with similar functions, such as web servers.

1. From the Azure portal menu, select + **Create a resource** > **Networking** > **Application security group,** or search for Application security group in the portal search box.
   
2. Select **Create.**

3. On the **Basics** tab of **Create an application security group,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **myResourceGroup.**|
   |**Instance details**|
   |Name|Enter myAsgWebServers.|
   |Region|Select **(US) East US.**|  
    
4. Select the **Review + create** tab, or select the blue **Review + create** button at the bottom of the page.

5. Select **Create.**

6. Repeat the previous steps, specifying the following values:
    
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **myResourceGroup.**|
   |**Instance details**|
   |Name|Enter myAsgMgmtServers.|
   |Region|Select **(US) East US.**|

7. Select the **Review + create** tab, or select the blue **Review + create** button at the bottom of the page.

8. Select **Create.**

### Exercise 3: Create a network security group.

#### Task 3: Use the Azure portal to create a network security group (NSG).

In this task, you will create a network security group (NSG) secures network traffic in your virtual network.

1. From the Azure portal menu, select + **Create a resource** > **Networking** > **Network security group,** or use the portal search box to search for **Network security group** (not Network security group (classic).
   
2. Select **Create.**

3. On the **Basics** tab of **Create network security group,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **myResourceGroup.**|
   |**Instance details**|
   |Name|Enter myNSG.|
   |Region|Select **(US) East US.**|  
    
4. Select the **Review + create** tab, or select the blue **Review + create** button at the bottom of the page.

5. Select **Create.**

### Exercise 4: Associate network security group to subnet.

#### Task 4: Use the Azure portal to create a network security group (NSG).

In this task, you'll associate the network security group with the subnet of the virtual network you created earlier.

1. From the Azure portal menu, search for myNsg in the portal search box.
   
2. Select **Subnets** from the **Settings** section of **myNSG.**

3. In the **Subnets** page, select + **Associate:**

4. Under **Associate subnet,** select **myVNet** for **Virtual network.**

5. Select **default*** for **Subnet,** and then select **OK.**

### Exercise 5: Create security rules.

#### Task 5: Use the Azure portal to create security rules

In this task, you'll create security rules for the network security group with the subnet of the virtual network you created earlier.

1. Select **Inbound security rules** from the **Settings** section of **myNSG.**
   
2. In **Inbound security rules** page, select + **Add:**

3. Create a security rule that allows ports 80 and 443 to the **myAsgWebServers** application security group. In **Add inbound security rule page,** enter or select this information:

   |Setting|Value|
   |---|---|
   |Source|Leave the default of **Any.**|
   |Source port ranges|Leave the default of **(*).**|
   |Destination|Enter myNSG.|
   |Destination application security groups|Select **Application security group.**|
   |Service|Leave the default of **Custom.**|
   |Destination port ranges|Enter 80,443.|
   |Protocol|Select **TCP.**|
   |Action|Leave the default of **Allow.**|
   |Priority|Leave the default of **100.**|
   |Name|Enter Allow-Web-All.|

4. Select **Add.**

5. Complete steps 3-4 again using this information:

   |Setting|Value|
   |---|---|
   |Source|Leave the default of **Any.**|
   |Source port ranges|Leave the default of **(*).**|
   |Destination|Select **Application security group.**|
   |Destination application security group|Select **myAsgMgmtServers.**|
   |Service|Leave the default of **Custom.**|
   |Destination port ranges|Enter 3389.|
   |Protocol|Select **Any.**|
   |Action|Leave the default of **Allow.**|
   |Priority|Leave the default of **110.**|
   |Name|Enter Allow-RDP-All.|
   
6. Select **Add.**

### Exercise 6: Create virtual machines.

#### Task 6: Use the Azure portal to create virtual machines

In this task, you'll create two virtual machines (VMs) in the virtual network you created earlier.

1. From the Azure portal menu, select + **Create a resource** > **Compute** > **Virtual machine,** or search for Virtual machine in the portal search box.
   
2. In **Create a virtual machine,** enter or select this information in the **Basics** tab:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Resource group|Select **myResourceGroup.**|
   |**Instance details**|
   |Virtual machine name|Enter myVMWeb.|
   |Region|Select **(US) East US.**|
   |Availability options|Leave the default of **No infrastructure redundancy required.**|
   |Security type|Leave the default of **Standard.**|
   |Image|Select **Windows Server 2019 Datacenter - Gen2.**|
   |Image|Select **Standard_DS2_V3.**|
   |**Administrator account**|
   |Username|Enter a username.|
   |Username|Enter a password.|
   |Confirm password|Reenter password.|
   |**Inbound port rules**|
   |Select inbound ports|Select **None.**|

3. Select the **Networking** tab.

4. In the **Networking** tab, enter or select the following information:

   |Setting|Value|
   |---|---|
   |**Network interface**|
   |Virtual network|Select **myVNet.**|
   |Subnet|Select **default (10.0.0.0/24).**|
   |Public IP|Leave the default of a new public IP.|
   |NIC network security group|Select **None.**|
   
5. Select the **Review + create** tab, or select the blue **Review + create** button at the bottom of the page.

6. Select **Create.** The VM may take a few minutes to deploy.
  
   Create the second virtual machine

   Complete steps 1-6 again, but in step 2, enter myVMMgmt for Virtual machine name.

   Wait for the VMs to complete deployment before advancing to the next section.

### Exercise 7: Associate network interfaces to an ASG.

#### Task 7: Use the Azure portal to create virtual machines

In this task, you'll add the network interface of each VM to one of the application security groups you created previously:

1. Search for myVMWeb in the portal search box.
   
2. Select **Networking** from the **Settings** section of **myVMWeb** VM.

3. Select the **Application security groups** tab, then select **Configure the application security groups.**

4. In **Configure the application security groups,** select **myAsgWebServers.** Select **Save.**

5. Complete steps 1 and 2 again, searching for the myVMMgmt virtual machine and selecting the **myAsgMgmtServers** ASG.

### Exercise Test traffic filters.

#### Task 7: Use the Azure portal to Test traffic filters

In this task, you'll test traffic filters for the previuosly created myVMWeb web server. 

1. Search for myVMMgmt in the portal search box.
   
2. On the **Overview** page, select the **Connect** button and then select **RDP.**

3. Select **Download RDP file.**

4. Open the downloaded rdp file and select **Connect.** Enter the username and password you specified when creating the VM.

5. Select **OK.**

6. You may receive a certificate warning during the connection process. If you receive the warning, select **Yes** or **Continue,** to continue with the connection.

   The connection succeeds, because inbound traffic from the internet to the **myAsgMgmtServers** application security group is allowed through port 3389.

   The network interface for **myVMMgmt** is associated with the **myAsgMgmtServers** application security group and allows the connection.

7. Open a PowerShell session on **myVMMgmt.** Connect to **myVMWeb** using the following:

    ```powershell
    mstsc /v:myVmWeb
    ```
    
   The RDP connection from **myVMMgmt** to **myVMWeb** succeeds because virtual machines in the same network can communicate with each other over any port by default.

   You can't create an RDP connection to the **myVMWeb** virtual machine from the internet. The security rule for the **myAsgWebServers** prevents connections to port 3389 inbound from the internet.
   Inbound traffic from the Internet is denied to all resources by default.

8. To install Microsoft IIS on the **myVMWeb** virtual machine, enter the following command from a PowerShell session on the **myVMWeb** virtual machine:

      ```powershell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```

9. After the IIS installation is complete, disconnect from the **myVMWeb** virtual machine, which leaves you in the **myVMMgmt** virtual machine remote desktop connection.

10. Disconnect from the **myVMMgmt** VM.

11. Search for *myVMWeb* in the portal search box.

12. On the **Overview** page of **myVMWeb,** note the **Public IP address** for your VM.

13. To confirm that you can access the **myVMWeb** web server from the internet, open an internet browser on your computer and browse to http://<public-ip-address-from-previous-step>.

    You see the IIS default page, because inbound traffic from the internet to the **myAsgWebServers** application security group is allowed through port 80.

    The network interface attached for **myVMWeb** is associated with the **myAsgWebServers** application security group and allows the connection.

   
   
    > **Note**: Ut feugiat est id ultrices gravida.

1. Phasellus urna lacus, luctus at suscipit vitae, maximus ac nisl. 

    - Morbi in tortor finibus, tempus dolor a, cursus lorem. 

    - Maecenas id risus pharetra, viverra elit quis, lacinia odio. 

    - Etiam rutrum pretium enim. 

1. Curabitur in pretium urna, nec ullamcorper diam. 

#### Review

Maecenas fringilla ac purus non tincidunt. Aenean pellentesque velit id suscipit tempus. Cras at ullamcorper odio.
