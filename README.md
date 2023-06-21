# Vulnerability Management Lab

![Vuknerability Management](https://i.imgur.com/sGOOt8J.jpg)

## Introduction

For this project, I aimed to establish a secure network within Azure and effectively manage vulnerabilities. It invlived deploying an OpenVAS Vulnerability Management Scanner VM and creating a purposely vulnerable Windows 10 VM. Vulnerability scans were performed using OpenVAS, and the results were analyzed to understad the impact of different scanning methods. Identified vulnerabilities were remediated, and realistic scenarios were simulated to evaluate the effectiveness of remediation efforts. 


## Technologies, Regulations, and Azure Components

- Azure
- Virtual Machines ((1) Windows (vulnerable-VM), (1) Linux utilizing OpenVAS)
- WIndows Remote Desktop for Remote Access
- PowerShell(Windows OS) or Terminal(MacOS)

  
## Methodology

- Setting up a secure Azure network: Establishing a secure network environment within the Azure platform.
- Utilizing an OpenVAS Vulnerability Management Scanner VM: Deploying and utilizing the OpenVAS scanner for vulnerability management purposes.
- Developing a vulnerable Windows 10 VM: Creating a purposely vulnerable Windows 10 virtual machine with outdated software and disabled security controls.
- Performing vulnerability scans: Conducting both unauthenticated and credentialed vulnerability scans using OpenVAS to identify potential security weaknesses.
- Analyzing scan results: Analyzing the scan results to gain insights into the vulnerabilities detected and understanding the differences between unauthenticated and credentialed scans.
- Remediation of identified vulnerabilities: Addressing and resolving the identified vulnerabilities based on the scan results.
- Simulating realistic vulnerability remediation scenarios: Creating a list of remediable vulnerabilities to simulate practical scenarios and evaluate the effectiveness of vulnerability remediation efforts.

  
## Unathenticated Scan of Vulnerable VM
![Unathenticated Scan](https://i.imgur.com/Nibkx9t.png)
Prior to Implementing Hardening Measures and Security Controls:

At the "BEFORE" stage of the project, the resources were deliberately set up with public exposure to the internet. This intentionally insecure configuration aimed to attract potential cyber attackers and monitor their techniques. The Virtual Machines had both their Network Security Groups (NSGs) and built-in firewalls configured with wide-open rules, granting unrestricted access from any source. Furthermore, all other resources, including storage accounts and databases, were deployed with public endpoints that were visible to the internet, without utilizing private endpoints for enhanced security.


## Architecture After Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/ch1cAMU.png)

The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

For the "BEFORE" metrics, all resources were originally deployed, exposed to the internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet; aka, no use for Private Endpoints.

In the "AFTER" stage, I implemented a series of measures to strengthen the security and protect the environment. These enhancements comprised the following:

- Network Security Groups (NSGs): I fortified the NSGs by configuring rules to block all inbound and outbound traffic, except for my own public IP address. This ensured that only authorized traffic from a trusted source was permitted to access the virtual machines.

- Built-in Firewalls: I fine-tuned the settings of the virtual machine's built-in firewalls to restrict access and prevent unauthorized connections. This involved adjusting the firewall rules based on the specific requirements of each virtual machine, minimizing the potential attack surface.

- Private Endpoints: To bolster the security of other Azure resources, I replaced the public endpoints with Private Endpoints. This transition restricted access to sensitive resources, such as storage accounts and databases, to the virtual network, isolating them from the public internet. This added layer of protection safeguarded the resources against unauthorized access and potential attacks.

By comparing the security metrics before and after implementing these hardening measures and security controls, I was able to demonstrate the effectiveness of each step in improving the overall security posture of the Azure environment.

## Attack Maps Before Hardening / Security Controls
- The showcased attack map serves as a visual representation of the repercussions caused by leaving the Network Security Group (NSG) open, enabling unrestricted flow of malicious traffic. This visualization emphasizes the significance of implementing adequate security measures, such as enforcing restrictive NSG rules. By doing so, unauthorized access can be prevented, and potential threats can be minimized effectively.
![NSG Allowed Inbound Malicious Flows](https://i.imgur.com/Aa8Nnjj.png) <br>

- The showcased attack map brings attention to the significant number of syslog authentication failures encountered by the Linux server that was deployed. These failures suggest unauthorized access attempts originating from external sources. This serves as a crucial reminder of the utmost importance of implementing robust authentication mechanisms to secure Linux servers and diligently monitoring system logs for any indications of intrusion attempts.
![Linux Syslog Auth Failures](https://i.imgur.com/ETLwFd9.png) <br>

- The showcased attack map presents multiple instances of RDP and SMB failures, illustrating the persistent efforts of potential attackers to exploit these protocols. This visualization strongly emphasizes the necessity of securing remote access and file sharing services to safeguard against unauthorized access and potential cyber threats. It highlights the critical importance of implementing robust security measures to protect these services and maintain a secure network environment.
![Windows RDP/SMB Auth Failures](https://i.imgur.com/7XXQ2xB.png) <br>

## Metrics Before Hardening / Security Controls

The following table shows the metrics I measured in my insecure environment for 24 hours:
Start Time 2023-06-16 5:17:32 AM
Stop Time 2023-06-17 5:17:32 AM

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 139088
| Syslog                   | 6035
| SecurityAlert            | 10
| SecurityIncident         | 341
| AzureNetworkAnalytics_CL | 2526

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 2023-06-17 11:15:31 AM
Stop Time	2023-06-18 11:15:31 AM

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 12546
| Syslog                   | 25
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

## Conclusion

For this project, a mini honeynet was constructed in Microsoft Azure, and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was utilized to activate alerts and generate incidents based on the collected logs. Furthermore, security metrics were assessed in the insecure environment prior to implementing security controls, and then once again after the implementation of these measures. It is important to highlight that the number of security events and incidents significantly decreased after the security controls were implemented, providing evidence of their effectiveness.

It is worth mentioning that if the network resources were extenzively used by regular users, it is probable that more security events and alerts could have been generated within the 24-hour period following the implementation of the security controls.
