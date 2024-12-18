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
  - Create a Resource Group<br />
      <img src=https://github.com/user-attachments/assets/0ddab006-9e9a-4565-a655-dfcf305138c5>
  - Create a Virtual Network<br />
      <img src=https://github.com/user-attachments/assets/1769fe82-8389-44b7-9841-5a5328afb498>
  - Deploy DC-1 (Windows Server 2022)<br />
      <img src=https://github.com/user-attachments/assets/69feeab5-8739-4fae-bafe-e7ba67dc053f>
  - Deploy Client-1 (Windows 10)<br />
      <img src=https://github.com/user-attachments/assets/57d5a2bb-f639-4721-af4c-683365f36d65>
<br />
<br />

2. Configure DC-1:
  - Set a static private IP for DC-1’s NIC<br />
      ![image](https://github.com/user-attachments/assets/f56dd0db-6beb-4208-be40-51a49ea7ee21)
  - Disable the Windows Firewall for connectivity testing (make sure the Public Profile is also turned off!)<br />
      ![image](https://github.com/user-attachments/assets/d2b55213-7ee3-4616-ba83-47020f0a518c)
<br />
<br />

3. Configure Client-1:
  - Set Client-1’s DNS settings to DC-1’s private IP.<br />
      ![image](https://github.com/user-attachments/assets/9c5750ac-1975-4c79-8718-f627b729bfc6)
  - Verify DNS resolution and connectivity using ping.<br />
      ![image](https://github.com/user-attachments/assets/57562cb9-3569-4a9b-b896-219dde1caa60)
  - Running ipconfig /all will show the DNS settings now applied as DC-1's private IP address<br />
      ![image](https://github.com/user-attachments/assets/0975b8b1-2a65-410c-8441-cadd29cd2ceb)
<br />
<br />

4. Error at Step 3? Check Network Security Group (NSG):
  - If you get an error message when trying to apply step 3, ensure port 53 (DNS) is allowed in inbound and outbound rules for both DC-1 and Client-1.
    - Search for "Network security groups" in Azure and click into "Network security groups" when it comes up. Not the classic version.
    - Click into "client-1-nsg" (or whatever you have it named) and do the following steps:
      - Click the "Settings" dropdown menu
      - Click "Inbound security rules"
      - Click "Add"
      - Leave everything alone except in the "Destination port ranges" field; change the number to 53 and in the "Priority" field change it to 290
      - Click the "Save" button
      - Then click "Outbound security rules" and complete the same process again
    - Then click into "dc-1-nsg" and do the same process again.
    - Go to "Virtual machines"
    - Click the checkbox next to "client-1" and "dc-1" and click "Restart" in the top bar
<br />
<br />
