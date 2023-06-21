# Vulnerability Management Lab

![Vuknerability Management](https://i.imgur.com/sGOOt8J.jpg)

## Introduction

For this project, I aimed to establish a secure network within Azure and effectively manage vulnerabilities. It involved deploying an OpenVAS Vulnerability Management Scanner VM and creating a purposely vulnerable Windows 10 VM. Vulnerability scans were performed using OpenVAS, and the results were analyzed to understad the impact of different scanning methods. Identified vulnerabilities were remediated, and realistic scenarios were simulated to evaluate the effectiveness of remediation efforts. 


## Technologies, Regulations, and Azure Components

- Azure
- Virtual Machines ((1) Windows 10 (vulnerable-VM), (1) Linux utilizing OpenVAS)
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
![Unauthenticated scan](https://i.imgur.com/Nibkx9t.png)
![Unathenticated Scan](https://i.imgur.com/RrwniOz.png)
Prior to Implementing Hardening Measures and Security Controls:

At the "BEFORE" stage of the project, the resources were deliberately set up with vulnerable applications. These intentionally insecure applications aimed to allow the scanner to perform an unathenticated scan to identify vulnerablities within the system. The Windows Virtual Machine had its firewall disabled and vulnerable out of date applications such as Adobe, Mozilla Firefox, and VLC playerboth installed. 

```Unathenticated scans provide an overview of the vulnerabilities that can be identified without accessing the internal compnents of the target system. It helps to identify vulnerabilities that can be detected externally and helps assess the overall security posture of the system from an outsiders perspective. Note, this type of scan cannot uncover vulnerabilities that require authenticated access```

```In the above image, notice that the out-of-date software does not show up in the report. That is due to the fact that the scanner did not do an authenticated scan, the scan was not able to deep dive into the system and scan all files and registries```

## Authenticated(credentialed) Scan of Vulnerable VM
![Credentialed scan](https://i.imgur.com/gv3WadH.png)
![Credentialed scan](https://i.imgur.com/UNJ6gkR.png)


For the "BEFORE" metrics, the VM was originally deployed, exposed to the internet with vulnerable software downloaded. 

In the "AFTER" stage, I conducted a credentialed scan that took a deep dive into the system to identify any vulnerabilities.

```Credentialed scanning is a process of conducting vulnerability scans with authenticated access to the target system by user providing valid credentials such as usernames and passwords to the scanning tool. The scanner can then deep dive into the systems internal components and configurations such as accessing system files, evaluate patch levels, assess user permissions,and discover hidden vulnerabilities allowing for a more thorough assessment of vulnerabilities```





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
