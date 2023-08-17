---
lab:
    title: 'Exercise 02b - Enable just-in-time access on VMs'    
    module: 'Module 02 - Configure just-in-time (JIT) VM access in Defender for Cloud'
---

You can use Microsoft Defender for Cloud's just-in-time (JIT) access to protect your Azure virtual machines (VMs) from unauthorized network access. Many times firewalls contain allow rules that leave your VMs vulnerable to attack. JIT lets you allow access to your VMs only when the access is needed, on the ports needed, and for the period of time needed. 

---

## Skilling tasks

- Enable JIT on your VMs from the Azure portal.

- Request access to a VM that has JIT enabled from the Azure portal.

## Exercise instructions 

### Enable JIT on your VMs from Microsoft Defender for Cloud.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. From Defender for Cloud's menu, open **Workload protections.**

4. Select **Just-in-time VM access.**

5. In the Not configured virtual machines, mark the VMs to protect with JIT and select **Enable JIT on VMs.**

   - SS - SSH (Secure Shell)
   - 3389 - RDP (Remote Desktop Protocol)
   - 5989 - WinRM (Windows Remote Management)
   - 5986 - WinRM (Windows Remote Management)

    To customize the JIT access:

   - Select **Add.**
     
   - Select one of the ports in the list to edit it or enter other ports. For each port, you can set the:
     
     - **Protocol** - The protocol that is allowed on this port when a request is approved
     - **Allowed source IPs** - The IP ranges that are allowed on this port when a request is approved
     - **Maximum request time** - The maximum time window during which a specific port can be opened
  
    - Selet **OK.**

6. To save the port configuration, select **Save.**     
     
### Edit the JIT configuration on a JIT-enabled VM using Defender for Cloud.

>**Note**: You can modify a VM's just-in-time configuration by adding and configuring a new port to protect for that VM, or by changing any other setting related to an already protected port.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. From Defender for Cloud's menu, open **Workload protections.**

4. Select **Just-in-time VM access.**

5. In the **JIT VM access configuration,** you can either edit the list of port or select **Add** a new custom port.

6. When you finish editing the ports, select **Save.**

### Request access to a JIT-enabled VM from Microsoft Defender for Cloud

>**Note**: When a VM has a JIT enabled, you have to request access to connect to it. You can request access in any of the supported ways, regardless of how you enabled JIT.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. From Defender for Cloud's menu, open **Workload protections.**

3. Select **Just-in-time VM access.**

4. From the **Just-in-time VM access** page, select the **Configured** tab.

5. Select the VMs you want to access.

    - The icon in the **Connection Details** column indicates whether JIT is enabled on the network security group or firewall. If it's enabled on both, only the firewall icon appears.

    - The **Connection Details** column shows the user and ports that can access the VM.

6. Select **Request access.** The **Request access** window opens.

7. Under **Request access,** select the ports that you want to open for each VM, the source IP addresses that you want the port opened on, and the time window to open the ports.

8. Select **Open ports.**

### Enable JIT on your VMs from Azure virtual machines

>**Note**: You can enable JIT on a VM from the Azure virtual machines pages of the Azure portal.

1. From the Azure portal, search for and select **Virtual machines.**
   
2. Select the virtual machine you want to protect with JIT.

3. In the menu, select **Configuration.**

4. Under **Just-in-time access,** select **Enable just-in-time.**

5. By default, just-in-time access for the VM uses these settings:

   - Windows machines
   
     - RDP port: 3389
     - Maximum allowed access: Three hours
     - Allowed source IP addresses: Any

   - Linux machines
     - SSH port: 22
     - Maximum allowed access: Three hours
     - Allowed source IP addresses: Any
   
6. By default, just-in-time access for the VM uses these settings:

   - From Defender for Cloud's menu, select **Just-in-time VM access.**
   - From the **Configured** tab, right-click on the VM to which you want to add a port, and select edit.
  
 ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/9034dc74-b865-4743-bcd6-8f0ae71a6d43)



   - Under **JIT VM access configuration,** you can either edit the existing settings of an already protected port or add a new custom port.
   - When you've finished editing the ports, select **Save.**   

### Request access to a JIT-enabled VM from the Azure virtual machine's connect page.

>**Note**: When a VM has a JIT enabled, you have to request access to connect to it. You can request access in any of the supported ways, regardless of how you enabled JIT.

1. Start a browser session and sign-in to the [Azure portal menu.](https://portal.azure.com/)
   
2. In the Azure portal, open the virtual machines pages.

3. Select the VM to which you want to connect, and open the **Connect** page.

   - Azure checks to see if JIT is enabled on that VM.

        - If JIT isn't enabled for the VM, you're prompted to enable it.
    
        - If JIT is enabled, select **Request access** to pass an access request with the requesting IP, time range, and ports that were configured for that VM.

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/948811f6-64d9-4454-ae84-d951ca01cbbf)



> **Results**: You have explored various methods on how to enable JIT on your VMs and how to request access to VMs that have JIT enabled in Microsoft Defender for Cloud.
