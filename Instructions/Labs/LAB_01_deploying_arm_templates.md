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

5. Select **Add.**

6. Complete steps 3-4 again using this information:


   

    > **Note**: Ut feugiat est id ultrices gravida.

1. Phasellus urna lacus, luctus at suscipit vitae, maximus ac nisl. 

    - Morbi in tortor finibus, tempus dolor a, cursus lorem. 

    - Maecenas id risus pharetra, viverra elit quis, lacinia odio. 

    - Etiam rutrum pretium enim. 

1. Curabitur in pretium urna, nec ullamcorper diam. 

#### Review

Maecenas fringilla ac purus non tincidunt. Aenean pellentesque velit id suscipit tempus. Cras at ullamcorper odio.
