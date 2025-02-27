# Monitoring Network Traffic with Azure VMs 🌐

## Overview
This project demonstrates my ability to set up and manage Azure Virtual Machines (VMs), configure network resources, and monitor various types of network traffic (ICMP, SSH, DHCP, DNS, and RDP) using Wireshark. By following this walkthrough, you’ll see how I leverage Azure infrastructure and network tools to analyze and troubleshoot network behavior, a critical skill for IT roles.

---

## 1. Setting Up Azure Resources

### Step 1: Create a Resource Group
- Log in to the Azure portal and navigate to the "Resource groups" section.
- Click "Create" and name your resource group (e.g., "NetworkMonitoringRG").
- Select your desired region and create the resource group.

![Alt text](https://i.imgur.com/TzV6cZw.png)

---

### Step 2: Create a Windows 10 Virtual Machine
- In the Azure portal, go to "Virtual machines" and click "Create."
- Choose "Windows 10" as the image, name your VM (e.g., "Win10VM"), and select the previously created Resource Group.
- Configure basic settings (e.g., size, username, password), and allow Azure to create a new Virtual Network (VNet) and Subnet during VM creation.

![Alt text](https://i.imgur.com/Dpil7Yn.png)

---

### Step 3: Create a Linux (Ubuntu) Virtual Machine
- Return to "Virtual machines" and click "Create" again.
- Select "Ubuntu Server" as the image, name your VM (e.g., "UbuntuVM"), and choose the same Resource Group and VNet as the Windows 10 VM.
- Configure basic settings (e.g., size, username, SSH key), and ensure it uses the same VNet for connectivity.

![Alt text](https://i.imgur.com/GgqYkYb.png)


---

## 2. Monitoring ICMP Traffic

### Step 5: Connect to the Windows 10 VM via Remote Desktop
- Use Remote Desktop Protocol (RDP) to connect to your Windows 10 VM using its public IP address.

![Alt text](https://i.imgur.com/mK7ClAK.png)

---

### Step 6: Install and Configure Wireshark
*Wireshark is a network protocol analyzer that allows users to capture and interactively browse the traffic running on a computer network.*

- Inside the Windows 10 VM, download and install Wireshark from its official website.
- Launch Wireshark and ensure it’s ready to capture network traffic.

![Alt text](https://i.imgur.com/UkompHb.png)

---

### Step 7: Filter and Observe ICMP Traffic
- In Wireshark, set a filter for `icmp` to monitor only ICMP traffic.
- Retrieve the private IP address of the Ubuntu VM from the Azure portal.
- From the Windows 10 VM, open Command Prompt or PowerShell and ping the Ubuntu VM’s private IP (e.g., `ping <Ubuntu_Private_IP>`).
- Observe ping requests and replies in Wireshark.

*Upload Image Here: Screenshot of Wireshark showing ICMP traffic between VMs.*

---

### Step 8: Ping a Public Website and Analyze Traffic
- From the Windows 10 VM, ping a public website (e.g., `ping www.google.com`).
- Watch the ICMP traffic in Wireshark to see how requests and replies interact with external networks.

*Upload Image Here: Screenshot of Wireshark capturing ICMP traffic to www.google.com.*

---

### Step 9: Test Network Security Group (NSG) Rules
- Initiate a continuous ping from the Windows 10 VM to the Ubuntu VM (e.g., `ping <Ubuntu_Private_IP> -t`).
- In the Azure portal, locate the NSG associated with the Ubuntu VM.
- Disable inbound ICMP traffic in the NSG rules.
- Return to the Windows 10 VM and observe the ping activity in both Wireshark and the command line (pings should fail).
- Re-enable ICMP traffic in the NSG.
- Observe pings resuming in Wireshark and the command line.
- Stop the ping activity with `Ctrl+C`.

*Upload Image Here: Screenshots showing NSG rule changes and Wireshark capturing the ICMP behavior before/after changes.*

---

## 3. Monitoring SSH Traffic

### Step 10: Filter and Observe SSH Traffic
- In Wireshark, set a filter for `tcp.port == 22` to monitor SSH traffic.
- From the Windows 10 VM, use an SSH client (e.g., PuTTY or Windows PowerShell) to connect to the Ubuntu VM’s private IP (e.g., `ssh username@<Ubuntu_Private_IP>`).
- Enter commands (e.g., username, password) and observe the SSH traffic in Wireshark.
- Exit the SSH session by typing `exit` and pressing Enter.

*Upload Image Here: Screenshot of Wireshark capturing SSH traffic during the connection.*

---

## 4. Monitoring DHCP Traffic

### Step 11: Filter and Observe DHCP Traffic
- In Wireshark, set a filter for `bootp` or `dhcp` to monitor DHCP traffic.
- From the Windows 10 VM, open Command Prompt and renew the IP address with `ipconfig /renew`.
- Observe the DHCP traffic in Wireshark as the VM requests and receives a new IP configuration.

*Upload Image Here: Screenshot of Wireshark capturing DHCP traffic during IP renewal.*

---

## 5. Monitoring DNS Traffic

### Step 12: Filter and Observe DNS Traffic
- In Wireshark, set a filter for `dns` to monitor DNS traffic.
- From the Windows 10 VM, use the `nslookup` command to query IP addresses for websites (e.g., `nslookup www.google.com` and `nslookup www.disney.com`).
- Observe the DNS queries and responses in Wireshark.

*Upload Image Here: Screenshot of Wireshark capturing DNS traffic for the nslookup commands.*

---

## 6. Monitoring RDP Traffic

### Step 13: Filter and Observe RDP Traffic
- In Wireshark, set a filter for `tcp.port == 3389` to monitor RDP traffic.
- Observe the continuous traffic in Wireshark while connected to the Windows 10 VM via RDP.
- Note: This traffic appears non-stop because RDP streams a live desktop session, constantly transmitting data between the client and server.

*Upload Image Here: Screenshot of Wireshark capturing continuous RDP traffic.*

---

## Conclusion
This project showcases my proficiency in configuring Azure VMs, managing network resources, and using Wireshark to analyze various types of network traffic. By demonstrating hands-on experience with ICMP, SSH, DHCP, DNS, and RDP traffic, I highlight my ability to troubleshoot, secure, and optimize network environments—valuable skills for any IT role.
