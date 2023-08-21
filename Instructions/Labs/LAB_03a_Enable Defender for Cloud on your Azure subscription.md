---
lab:
    title: 'Exercise 03a - Enable Defender for Cloud on your Azure subscription'
    module: 'Module 03 - Set up Microsoft Defender for Cloud'
---

The main goal of this exercise is to provide hands-on experience in configuring and enabling Microsoft Defender for Cloud within an Azure subscription. This will allow you to monitor and protect your cloud resources against security threats. 

---

## Skilling tasks

- Upgrade your subscription for Microsoft Defender for Cloud.
  
- Deploy the Microsoft Monitoring Agent to necessary machines for comprehensive coverage.

## Exercise instructions

### Upgrade Microsoft Defender for Cloud

1. Sign-in to the [Azure portal menu.](https://portal.azure.com/)

2. In the Azure portal, in the Search resources, services, and docs text box at the top of the Azure portal page, type Microsoft Defender for Cloud and press the Enter key.

3. On the Microsoft Defender for Cloud | Getting started blade, on the Upgrade tab >> scroll down until the **Select susbscriptions and workspaces to protect with enhanced security features** section is visible >> turn on the **Microsoft Defender plan** by selecting your your **Subscription** and the **Log Analytics Workspace** you created in Module 02, then click the large blue **Upgrade button.** at the bottom of the page.

4. On the Microsoft Defender for Cloud | Getting started blade, in the Install agents tab, scroll down and **check** the box that is associated with the subscription on which agents will be installed and click **Install agents.**

> **Results**: You have upgraded and enabled Defender for Cloud on your Azure subscription.
