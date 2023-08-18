---
lab:
    title: 'Exercise 04 - Collect data from your workloads with the Log Analytics agent'    
    module: 'Module 04 - Configure and integrate a Log Analytics agent and workspace in Defender for Cloud'
---

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

7. From the Configuration options pane, click **Edit configuration.**

8. In the Auto-provisioning configuration template complete the following actions:

   - Under Workspace selection, click **Custom workspace.**

   - Click the dropdown menu and select your previously created workspace.

   - Under Security events storage, click the dropdown menu and, select **All Events.**

   - At the bottom of the Auto-provisioning template, click **Apply.**
   
![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/15b601fa-0426-4258-bdb1-8741107aa3a1)




> **Results**: You have configured the Log Analytics agent and workspace in Microsoft Defender for Cloud.
