# FUTURE_CS_03# 

Task 3: Home Wi-Fi Security Assessment (MiFi-Based)

This repository details a Wi-Fi security assessment conducted on a home network using a MiFi router, as part of an internship to evaluate common wireless network vulnerabilities and provide actionable security recommendations.

## Table of Contents

  * Overview
  * Skills Gained
  * Tools Used
  * Network Environment
  * Assessment Methodology
      * Device Discovery & Unauthorized Device Check
      * Port Scan for Open Services
      * Password Strength Evaluation
      * Network Traffic Analysis
  * Summary of Findings
  * Recommendations
  * Notes on Limitations
  * Author
  * Deliverables

## Overview
The objective of this task was to conduct a comprehensive Wi-Fi security assessment on a home network utilizing a Setout MiFi 4G LTE router. The assessment aimed to evaluate password strength, identify open ports and unauthorized devices, and analyze network traffic to uncover potential vulnerabilities. The ultimate goal was to provide actionable recommendations to enhance the network's security posture.

## Skills Gained

Through this assessment, I gained practical experience and enhanced my skills in:

  * **Wireless Network Security:** Understanding common Wi-Fi vulnerabilities and attack vectors.
  * **Network Scanning & Analysis:** Proficiency in using tools like Nmap and Wireshark for network reconnaissance and traffic analysis.
  * **Vulnerability Assessment:** Identifying weaknesses in network configurations and password policies.
  * **Security Recommendations:** Formulating clear and actionable advice for improving network security.
  * **Kali Linux Proficiency:** Practical application of Kali Linux for security assessments.

## Tools Used

The following tools were utilized during the Wi-Fi security assessment:

  * **Nmap:** Used for network scanning and detecting open ports and services and utilized for device discovery and identifying devices connected to the local network.
  * **Wireshark:** Employed for packet capture and protocol analysis to inspect network traffic.
  * **Aircrack-ng:** Used for simulated WPA handshake cracking to evaluate password strength.
  * **Kali Linux 2025.2:** The operating system used as the assessment environment.

## Network Environment

  * **Router:** Setout MiFi 4G LTE (Mobile Hotspot) 
  * **Local Subnet:** 192.168.100.x/24 
  * **Access Mode:** Wireless
  * **Hardware Limitation:** The MiFi router lacked monitor mode capabilities, which influenced the assessment methodology

## Assessment Methodology

### Device Discovery & Unauthorized Device Check

The `sudo nmao -sn 192.168.100.x` command was executed to discover devices on the network. The results identified the My kali (IP: 192.168.100.xxx, MAC: 00:11:22:33:44:55) and a User Phone (IP: 192.168.100.xxx, MAC: 4C:E0:DB:A7:AC:19). No unauthorized devices were detected

### Port Scan for Open Services

An Nmap scan (`nmap -sV -p-192.168.100.x`) was performed to identify open ports and services on the MiFi router. The following open ports were detected:

  * **80/tcp:** Open, running an HTTP service (Huawei Web UI).
  * **53/tcp:** Open, indicating a DNS Service.
  * **49152/tcp:** Open, identified as Huawei uPnP.

**Observation:** The presence of UPnP (Universal Plug and Play) enabled by default was noted as a potential attack vector.

### Password Strength Evaluation

Due to the MiFi's hardware limitations (lack of monitor mode and handshake capture), an alternative approach was adopted for password evaluation. A manual audit of the WPA2 key, "MySecure Pass2024\!", revealed it to be 16 characters in length and of strong complexity.

### Network Traffic Analysis

Wireshark was used on `wlan0` in station mode for network traffic analysis.

  * **Findings:** Traffic capture was limited to the assessment device due to client isolation. Plaintext DNS queries (unencrypted) were detected. No suspicious connections were observed.

## Summary of Findings

The assessment yielded the following key findings:

  * **Unauthorized Devices:** None found.
  * **Open Ports:** UPnP was noted as open on the MiFi.
  * **Password Strength:** The current WPA2 password was deemed strong.
  * **Traffic Analysis:** No issues were detected, though plaintext DNS queries were observed.

## Recommendations

Based on the assessment, the following recommendations are provided to enhance the Wi-Fi network's security:

1.  **Disable UPnP:** Disable Universal Plug and Play if it is not explicitly required, as it can be a potential attack vector.
2.  **Use Strong Passwords:** Continue to use strong WPA2/WPA3 passwords.
3.  **Regular Password Changes:** Change Wi-Fi passwords regularly to mitigate risks.
4.  **Monitor Connected Devices:** Periodically monitor devices connected to the network to identify any unauthorized connections.
5.  **Consider Router Upgrade:** For enhanced control and advanced security features, consider upgrading to a full-featured router.

## Notes on Limitations

It's important to note the inherent limitations of the MiFi router, which lacks monitor mode. The assessment methodology was adjusted to accommodate these constraints, focusing on achievable reconnaissance and analysis techniques with the available tools.

