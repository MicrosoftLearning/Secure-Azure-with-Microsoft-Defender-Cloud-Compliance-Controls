---
lab:
    title: 'Exercise 04 - Enable just-in-time access on VMs'    
    module: 'Module 04 - Configure just-in-time (JIT) VM access in Defender for Cloud'
---

Defender for Cloud collects data from your Azure virtual machines (VMs), Virtual Machine Scale Sets, IaaS containers, and non-Azure (including on-premises) machines to monitor for security vulnerabilities and threats. Some Defender plans require monitoring components to collect data from your workloads. When the Log Analytics agent is on, Defender for Cloud deploys the agent on all supported Azure VMs and any new ones created. 

---

## Skilling tasks

- Use Log Analytics Agent defaults for your agent type.

- Select your workspace.
  
- Define the level of security event data to store at the workspace level.

## Exercise instructions 

### Enable JIT on your VMs from Microsoft Defender for Cloud.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. From Defender for Cloud's menu, open **Workload protections.**

4. Select **Just-in-time VM access.**

5. In the Not configured virtual machines, mark the VMs to protect with JIT and select **Enable JIT on VMs.**

   - SS - SSH
   - 3389 - RDP
   - 5989 - WinRM
   - 5986 - WinRM

    To customize the JIT access:

   - Select **Add.**
     
     - Select one of the ports in the list to edit it or enter other ports. For each port, you can set the:
     - Protocol - The protocol that is allowed on this port when a request is approved
     - Allowed source IPs - The IP ranges that are allowed on this port when a request is approved
     - Maximum request time - The maximum time window during which a specific port can be opened
  
   - Select **OK.**

7. To save the port configuration, select **Save.**

8. From the Configuration options pane, click **Edit configuration.**

9. In the Auto-provisioning configuration template complete the following actions:
   
   	- Under Workspace selection, click **Custom workspace.**
   	- Click the dropdown menu and select your previously created workspace.
   	- Under Security events storage, click the dropdown menu and, select **All Events.**
   	- At the bottom of the Auto-provisioning template, click **Apply.**
   
![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/30e84cba-9cb5-4d0a-8a88-6a48b8a5820f)


> Results: You have configured the Log Analytics agent and workspace in Microsoft Defender for Cloud.
