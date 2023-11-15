---
lab:
    title: 'Exercise 04 - Collect data from your workloads with the Log Analytics agent'    
    module: 'Module 04 - Configure and integrate a Log Analytics agent and workspace in Defender for Cloud'
---


>**Note**: To complete this lab, you will need an [Azure subscription.](https://azure.microsoft.com/en-us/free/?azure-portal=true) in which you have administrative access. 


Defender for Cloud collects data from your Azure virtual machines (VMs), Virtual Machine Scale Sets, IaaS containers, and non-Azure (including on-premises) machines to monitor for security vulnerabilities and threats. Some Defender plans require monitoring components to collect data from your workloads. When the Log Analytics agent is on, Defender for Cloud deploys the agent on all supported Azure VMs and any new ones created. 

---

## Skilling tasks

- Use Log Analytics Agent defaults for your agent type.

- Select your workspace.
  
- Define the level of security event data to store at the workspace level.

## Exercise instructions 

### Configure integration with the Log Analytics agent.

>**Note**: When the Log Analytics agent is on, Defender for Cloud deploys the agent on all supported Azure VMs and any new ones created. 

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. From Defender for Cloud's menu, open **Environment settings.**

4. Select the your subscription.

5. In the Settings & monitoring Coverage column of the Defender plans, select **Settings & monitoring.**

7. In the Log Analytics list, in the Configuration column, click **Edit configuration.**

8. In the Auto-provisioning configuration template complete the following actions:

   - Under Workspace selection, click **Custom workspace.**

   - Click the **dropdown menu** and **select** your previously created workspace.

   - Under **Security events storage**, click the **dropdown menu** and, select **All Events.**

   - At the bottom of the Auto-provisioning template, click **Apply.**
   
![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/c1c812e7-b5ca-4caa-b8e6-34a6e4b325fd)




> **Results**: You have configured the Log Analytics agent and workspace in Microsoft Defender for Cloud.
