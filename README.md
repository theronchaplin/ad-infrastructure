<img src=https://github.com/user-attachments/assets/b0b2b2d4-c2ed-47b6-b59c-9da1d87514c6>
<br />
<br />

<h1>Preparing AD Infrastructure in Azure</h1>

This section involves setting up the foundational environment for Active Directory within Azure. The lab includes creating a domain controller (DC-1) and a client machine (Client-1) in the same virtual network, configuring network settings, and verifying connectivity between the machines.<br />
<br />
<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Services
- PowerShell
<br />
<br />

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)
<br />
<br />

<h2>Walkthrough Steps</h2>

1. Create Resources:
  - Create a Resource Group, Virtual Network, and Subnet in Azure.
  - Deploy DC-1 (Windows Server 2022) and Client-1 (Windows 10).
<br />
<br />

2. Configure DC-1:
  - Set a static private IP for DC-1’s NIC.
  - Disable the Windows Firewall for connectivity testing.
<br />
<br />

3. Configure Client-1:
  - Set Client-1’s DNS settings to DC-1’s private IP.
  - Verify DNS resolution and connectivity using ping.
<br />
<br />

4. Check Network Security Group (NSG):
  - Ensure port 53 (DNS) is allowed in inbound and outbound rules for both DC-1 and Client-1.
<br />
<br />
