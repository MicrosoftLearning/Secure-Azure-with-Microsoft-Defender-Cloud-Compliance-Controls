---
lab:
    title: 'Exercise 06 - Enable just-in-time access on VMs'    
    module: 'Module 06 - Configure Azure Key Vault networking settings'
---

You can use the Azue portal to configure the Azure Key Vault networking settings to work with other applications and Azure services. 

---

## Skilling tasks

- Add an exsiting virtual network to a firewall and virtual network rules.

- Configure a virtual network and subnet to allow access to a key vault.

## Exercise instructions 

### Enable JIT on your VMs from Microsoft Defender for Cloud.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
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
  
   - Select **OK.**
  
6. To save the port configuration, select **Save.**     
     
### Edit the JIT configuration on a JIT-enabled VM using Defender for Cloud.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. From Defender for Cloud's menu, open **Workload protections.**

4. Select **Just-in-time VM access.**

5. In the **JIT VM access configuration,** you can either edit the list of port or select **Add** a new custom port.

6. When you finish editing the ports, select **Save.**

### Request access to a JIT-enabled VM from Microsoft Defender for Cloud

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. From Defender for Cloud's menu, open **Workload protections.**

3. Select **Just-in-time VM access.**

4. From the **Just-in-time VM access** page, select the **Configured** tab.

5. Select the VMs you want to access.

    - The icon in the **Connection Details** column indicates whether JIT is enabled on the network security group or firewall. If it's enabled on both, only the firewall icon appears.

    - The **Connection Details** column shows the user and ports that can access the VM.

6. Select **Request access.** The **Request access** window opens.

7. Under **Request access,** select the ports that you want to open for each VM, the source IP addresses that you want the port opened on, and the time window to open the ports.

8. Select **Open ports.**

### Request access to a JIT-enabled VM from the Azure virtual machine's connect page.

1. Start a browser session and sign-in to the Azure portal https://portal.azure.com/.
   
2. In the Azure portal, open the virtual machines pages.

3. Select the VM to which you want to connect, and open the **Connect** page.

   - Azure checks to see if JIT is enabled on that VM.

        - If JIT isn't enabled for the VM, you're prompted to enable it.
    
        - If JIT is enabled, select **Request access** to pass an access request with the requesting IP, time range, and ports that were configured for that VM.

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/ec7aeb31-296e-4093-ab53-85eb348469ad)

> Results: You have enabled JIT on your VMs and requested access to VMs that have JIT enabled in Microsoft Defender for Cloud.
