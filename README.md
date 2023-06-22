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

## Authenticated(credentialed) Re-Scan of Remediated Vulnerabilities
![Credentialed re-scan](https://i.imgur.com/mm2tYr0.png)
![Credentialed re-scan](https://i.imgur.com/GKxZ8e3.png)

The vulnerabilities were remediated by updating the software.



## Conclusion

For this project, the overarching objective was to enhance the understanding of vulnerability management, demonstrate proficiency in utiliing security tools liek OpenVAS, and develop skills in identifying, analyzing, and remediating vulnerabilities within a secure network environment.
