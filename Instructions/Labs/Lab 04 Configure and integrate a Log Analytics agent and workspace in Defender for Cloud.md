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

8. In the Auto-provisioning configuration template complete the following:
   a. Under Workspace selection, click **Custom workspace.**
   b. Click the dropdown menu and select your previously created workspace.
   c. Under Security events storage, click the dropdown menu and, select **All Events.**
   d. At the bottom of the Auto-provisioning template, click **Apply.**
   
![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/a3c06df7-c708-4928-a14d-55a5a04c5037)


     
11. Settings & monitoring Coverage column of the Defender plans, select **Settings & monitoring.**

12. On the **Basics** tab of **Create Log Analytics workspace,** enter or select this information:
   
   |Setting|Value|
   |---|---|
   |**Project details**|
   |Subscription|Select your subscription.|
   |Resource group|Enter *myResourceGroup.* Select **OK**|
   |**Instance details**|
   |Name|Enter *myWorkspace.*|
   |Region|Select **(US) East US.**|

11. Select the **Review + create tab,** or select the blue Review + create button at the bottom of the page.
  
12. Select **Create.**

> **Results:** You have created a Log Analytics workspace, to collect data from Azure reources, and diagnostics or log data from Azure Storage.












## Instructions

### Before you start

#### Setup Task

1. Integer dolor purus, gravida eu sem id, efficitur aliquet neque. 

1. Suspendisse viverra mauris in metus laoreet consectetur. 

1. Sed diam risus, convallis quis condimentum at, egestas malesuada libero. 

### Exercise 0: 

#### Task 0: 

1. Quisque dictum convallis metus, vitae vestibulum turpis dapibus non.

    1. Suspendisse commodo tempor convallis. 

    1. Nunc eget quam facilisis, imperdiet felis ut, blandit nibh. 

    1. Phasellus pulvinar ornare sem, ut imperdiet justo volutpat et.

1. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. 

1. Vestibulum hendrerit orci urna, non aliquet eros eleifend vitae. 

1. Curabitur nibh dui, vestibulum cursus neque commodo, aliquet accumsan risus. 

    ```
    Sed at malesuada orci, eu volutpat ex
    ```

1. In ac odio vulputate, faucibus lorem at, sagittis felis.

1. Fusce tincidunt sapien nec dolor congue facilisis lacinia quis urna.

    > **Note**: Ut feugiat est id ultrices gravida.

1. Phasellus urna lacus, luctus at suscipit vitae, maximus ac nisl. 

    - Morbi in tortor finibus, tempus dolor a, cursus lorem. 

    - Maecenas id risus pharetra, viverra elit quis, lacinia odio. 

    - Etiam rutrum pretium enim. 

1. Curabitur in pretium urna, nec ullamcorper diam. 

#### Review

Maecenas fringilla ac purus non tincidunt. Aenean pellentesque velit id suscipit tempus. Cras at ullamcorper odio.
