---
lab:
    title: 'Exercise 02 - Create a virtual network infrastructure'
    module: 'Module 03 - Filter network traffic with a network security group using the Azure portal'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


You can use a network security group to filter inbound and outbound network traffic to and from Azure resources in an Azure virtual network. Network security groups contain security rules that filter network traffic by IP address, port, and protocol. When a network security group is associated with a subnet, security rules are applied to resources deployed in that subnet.

## Architecture diagram

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/1bfec315-129b-48a9-9c35-1f21c837068f)

---

## Skilling tasks

- Create a network security group and security rules.
- Create application security groups.
- Create a virtual network and associate a network security group to a subnet.
- Deploy virtual machines and associate their network interfaces to the application security groups.

### Estimated Lab Duration: 20 minutes

## Exercise instructions 

### Create an azure resource group and virtual network.

>**Note**: The following task creates a virtual network with a resource subnet.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)             
   
2. In the search box at the top of the portal, type **virtual networks.** Select **Virtual networks** in the search results.

3. On the **Virtual networks** page, select + **Create.**

4. On the **Basics** tab of **Create virtual network**, enter or select the following information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Enter **az-rg-1.**|
   |**Instance details**|
   |Virtual network name|Enter **vnet-1.**|
   |Region|Select **(US) East US.**|  
    
5. Select **Next** to proceed to the **Security** tab.
  
6. Select **Next** to proceed to the **IP Addresses** tab.

7. In the address space box under **Subnets**, select the **default** subnet.

8. In **Edit subnet template**, enter or select the following information:

   |Setting|Value|
   |---|---|
   |**Subnet details**|
   |Subnet purpose|Leave the default setting as Default.|
   |Name|Enter **subnet-1.**|
   |Starting address|Leave the default setting as 10.0.0.0/16.|
   |Size|Leave the default settings as /24 (256 addresses).|

    ![image](https://github.com/user-attachments/assets/82076f64-6a7f-4235-942d-d83e32ed6ea1)

10. Select **Save.**

11. Select **Review + create** at the bottom of the screen, and when validation passes, select **Create.**

     ![image](https://github.com/user-attachments/assets/c53a04e4-d760-4e28-b998-1d48a56702f1)

### Create application security groups to enable you to group together servers with similar functions, such as web servers.

An application security group (ASGs) enables you to group together servers with similar functions, such as web servers.

1. In the search box at the top of the portal, enter **application security groups**. Select **Application security groups** in the search results.

2. On the **Application security groups** page, select **+ Create.**

3. On the **Basics** page of **Create an application security group**, enter or select the following information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |**Instance details**|
   |Name|Enter **asg-web.**|
   |Region|Select **East US.**|  
    
4. Select **Review + create.**

5. Select **Create.**

6. Repeat the previous steps, specifying the following values:
    
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |**Instance details**|
   |Name|Enter **asg-mgmt.**|
   |Region|Select **East US.**|

7. Select **Review + create.**

8. Select **Create.**

### Create a network security groug to secure network traffic in your virtual network.

A network security group (NSG) secures network traffic in your virtual network.

1. In the search box at the top of the portal, enter **network security groups**. Select **Network security groups** in the search results.

>**Note**: In the search results for Network security groups, you may see Network security groups (classic). Select Network security groups.

2. On the **Network security groups page**, select **+ Create.**

3. On the **Basics** tab of **Create network security group**, enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |**Instance details**|
   |Name|Enter **nsg-1.**|
   |Region|Select **East US.**|  
    
4. Select **Review + create**.

5. Select **Create.**

### Associate network security group to subnet

>**Note**: In this task, you associate the network security group with the subnet of the virtual network you created earlier.

1. In the search box at the top of the portal, enter **network security groups**. Select **Network security groups** in the search results.
   
2. Select **nsg-1.**

3. Select **Subnets** from the **Settings** section of **nsg-1.**

4. In the **nsg-1 | Subnets** page, select + **Associate:**

   ![image](https://github.com/user-attachments/assets/bfc18dd3-3345-4c05-9981-4f479d5f7c7e)

6. Under **Associate subnet,** select **vnet-1 (az-rg-1)** for **Virtual network.**

7. Select **subnet-1** for **Subnet**, and then select **OK.**

### Create security rules for the network security group with the subnet of the virtual network you created earlier.

1. Select **Inbound security rules** from the **Settings** section of **nsg-1.**
   
2. In **nsg-1 | Inbound security rules** page, select + **Add.**

3. Create a security rule that allows ports 80 and 443 to the **asg-web** application security group. In **Add inbound security rule** page, enter or select this information:

   |Setting|Value|
   |---|---|
   |Source|Leave the default of **Any.**|
   |Source port ranges|Leave the default setting port ranges.|
   |Destination|Select **Application security group.**|
   |Destination application security groups|Select **asg-web.**|
   |Service|Leave the default setting as Custom.|
   |Destination port ranges|Enter **80,443.**|
   |Protocol|Select **TCP.**|
   |Action|Leave the default settings as Allow.|
   |Priority|Leave the default setting as 100.|
   |Name|Enter **allowweball.**|

4. Select **Add.**

5. Complete previous steps with the following information:

   |Setting|Value|
   |---|---|
   |Source|Leave the default of **Any.**|
   |Source port ranges|Leave the default setting port ranges.|
   |Destination|Select **Application security group.**|
   |Destination application security group|Select **asg-mgmt.**|
   |Service|Select **RDP.**|
   |Destination port ranges|Leave the default setting as 3389.|
   |Protocol|Leave the default setting as TCP.|
   |Action|Leave the default setting as Allow.|
   |Priority|Leave the default setting as 110.|
   |Name|Enter **allowrdpall.**|
   
6. Select **Add.**

### Create two virtual machines (VMs) in the virtual network you created earlier.

1. In the search box at the top of the portal, enter **virtual machines.** Select **Virtual machines** in the search results.

2. In **Virtual machines**, select **+ Create**, then **Azure virtual machine.**
   
3. In **Create a virtual machine,** enter or select this information in the **Basics** page:

   |Setting|Value|
   |---|---|
   |**Project details**|
   |Susbcription|Select your subscription.|
   |Resource group|Select **az-rg-1.**|
   |**Instance details**|
   |Virtual machine name|Enter **vm-1.**|
   |Region|Select **(US) East US.**|
   |Availability options|From the Availability Zone drop-down menu, select **No infrastructure redundancy required.**|
   |Security type|From the Security type drop-down menu, select **Standard.**|
   |Image|From the Image drop-down menu, select **Windows Server 2022 Datacenter: Azure Edition - x64 Gen2.**|
   |VM architecture|Leave the default setting as x64.|
   |Run with Azure Spot discount|Leave the default setting as unchecked.|
   |Size|Leave the default setting as Standard_D2s_v3-2 vcpus, 8 GiB memory.|
   |**Administrator account**|
   |Username|Enter **Tenantadmin1.**|
   |Password|Enter **Superuser#150.**|
   |Confirm password|Reenter **Superuser#150.**|
   |**Inbound port rules**|
   |Public inbound ports|Select **None.**|
 
4. Select **Next: Disks** then **Next: Networking.**

5. In the **Networking** page, verify or enter the following information:

   |Setting|Value|
   |---|---|
   |**Network interface**|
   |Virtual network|Select **vnet-1.**|
   |Subnet|Leave the default setting as subnet-1 (10.0.0.0/24).|
   |Public IP|Leave the default setting as (new) vm-1-ip.|
   |NIC network security group|Select **None.**|
   
6. Select the **Review + create** button at the bottom of the page to proceed.

7. Select **Create.** The VM may take a few minutes to deploy.
  
   - Create the second virtual machine.

   - Repeat the previous steps to create a second virtual machine named **vm-2.**

   - Wait for the VMs to complete deployment before advancing to the next section.

### Associate network interfaces to an application security group

>**Note**: When you created the VMs, Azure created a network interface for each VM, and attached it to the VM. Add the network interface of each VM to one of the application security groups you created previously:

1. In the search box at the top of the portal, enter **virtual machines.** Select **Virtual machines** in the search results.

2. Select **vm-1.**
 
3. Select **Networking** from the section of **vm-1.**

4. Select **Application security groups** from the **Networking** section of **vm-1. Select **+ Add application security groups.**

5. From the **Add application security groups** template, select **asg-mgmt** from the **Application Security Groups** template, and then click the **Add** button at the bottom of the template page.

   ![image](https://github.com/user-attachments/assets/9bb38a91-8aa6-427b-9b6d-b01c5333ad4c)

7. Repeat previous steps for **vm-2**, selecting **asg-web** in the **Application security groups** template.

> **Results**: You have created a created a virtual network infrastructure and filtered network traffic with a network security group using the Azure portal.

> **Note**: Please do not remove the resources from this lab, as they are necessary for the following exercises: Exercise 05 - Enabling Just-in-Time Access on VMs, Exercise 06a - Configuring Key Vault Firewall and Virtual Networks.
