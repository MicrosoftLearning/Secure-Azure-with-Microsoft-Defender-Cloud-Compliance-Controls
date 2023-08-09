---
lab:
    title: '04 - Collect data from your workloads with the Log Analytics agent'    
    module: 'Module 04 - Configure and integrate a Log Analytics agent and workspace in Defender for Cloud'
---

# Lab 04: Collect data from your workloads with the Log Analytics agent
# Student lab manual

---
## Lab scenario

You can use a network security group to filter inbound and outbound network traffic to and from Azure resources in an Azure virtual network. Network security groups contain security rules that filter network traffic by IP address, port, and protocol. When a network security group is associated with a subnet, security rules are applied to resources deployed in that subnet.

---

## Skilling tasks

- Create a network security group and security rules
  
- Create application security groups
  
- Create a virtual network and associate a network security group to a subnet
  
- Deploy virtual machines and associate their network interfaces to the application security groups
  
- Test traffic filters

## Exercise instructions 

### Configure integration with the Log Analytics agent.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. From Defender for Cloud's menu, open **Environment settings.**

4. Select the your subscription.

5. In the Settings & monitoring Coverage column of the Defender plans, select **Settings & monitoring.**

7. From the Configuration options pane, click **Edit configuration.**

8. In the Auto-provisioning configuration template complete the following actions:
   
   	- Under Workspace selection, click **Custom workspace.**
   	- Click the dropdown menu and select your previously created workspace.
   	- Under Security events storage, click the dropdown menu and, select **All Events.**
   	- At the bottom of the Auto-provisioning template, click **Apply.**
   
![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/30e84cba-9cb5-4d0a-8a88-6a48b8a5820f)


> Results: You have enabled Defender for Cloud on your Azure subscription.
