---
lab:
    title: '01 - Create a workspace'
    module: 'Module 1: Create a Log Analytics workspace for Microsoft Defender for Cloud'
---

# Lab 01: Create a workspace
# Student lab manual

## Lab scenario

You can use a network security group to filter inbound and outbound network traffic to and from Azure resources in an Azure virtual network. 

Network security groups contain security rules that filter network traffic by IP address, port, and protocol. When a network security group is associated with a subnet, security rules are applied to resources deployed in that subnet.

## Skilling tasks

- Create a network security group and security rules
  
- Create application security groups
  
- Create a virtual network and associate a network security group to a subnet
  
- Deploy virtual machines and associate their network interfaces to the application security groups
  
- Test traffic filters

## Exercise instructions 

### Use the Log Analytics workspaces menu to create a workspace.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. From the Azure portal menu, enter **Log Analytics** in the search box. As you begin typing, the list filters based on your input. Select **Log Analytics workspaces.**

4. Select **Add.**

5. On the **Basics** tab of **Create Log Analytics workspace,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Enter *myResourceGroup.* Select **OK**|
   |**Instance details**|
   |Name|Enter *myWorkspace.*|
   |Region|Select **(US) East US.**|

6. Select the **Review + create tab,** or select the blue Review + create button at the bottom of the page.
  
8. Select **Create.**

> Results: You have created a Log Analytics workspace, to collect data from Azure reources, and diagnostics or log data from Azure Storage.
