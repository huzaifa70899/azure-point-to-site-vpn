# azure-point-to-site-vpn
Configured secure Point-to-Site VPN connection using Azure VPN Gateway and OpenVPN

# Azure Point-to-Site VPN Configuration

## Project Overview

This project demonstrates how to configure a **Point-to-Site (P2S) VPN connection in Microsoft Azure** to allow a remote client to securely connect to a private Azure Virtual Network.

The lab simulates a real-world enterprise scenario where employees working remotely must securely access internal infrastructure hosted in the cloud without exposing services to the public internet.

The VPN tunnel encrypts all communication between the client device and Azure network using the **OpenVPN protocol**.

---

## Real-World Scenario

Organizations often host sensitive infrastructure inside a **private Azure Virtual Network**, including:

- Internal web servers
- Databases
- File storage
- Active Directory domain controllers

For security reasons, these systems are not publicly accessible.

However, remote employees still need secure access to manage systems and use internal applications.

A **Point-to-Site VPN solution** allows employees to establish an encrypted tunnel from their local device to the company's Azure network, enabling secure remote access.

This project demonstrates how such a solution can be configured and tested.

---

## Technologies Used

- Microsoft Azure
- Azure Virtual Network
- Azure VPN Gateway
- OpenVPN Protocol
- Network Security Groups (NSG)
- Azure Portal

---

## Architecture

Client Computer  
↓  
Encrypted VPN Tunnel (OpenVPN)  
↓  
Azure VPN Gateway  
↓  
Azure Virtual Network  
↓  
Internal Azure Resources

---

## Configuration Steps

### 1. Create a Resource Group

Navigate to:

Azure Portal → Resource Groups → Create

Configuration:

- Resource Group Name: **RG-Azure-VPN-Lab**
- Region: **Canada Central**

Click **Review + Create**, then **Create**.

---

### 2. Create the Virtual Network

Navigate to:

Azure Portal → Virtual Networks → Create

Configuration:

- Name: **VNet-VPN-Lab**
- Region: **Canada Central**
- Address Space: **10.1.0.0/16**

Create the default subnet:

- Subnet Name: **default**
- Subnet Address Range: **10.1.1.0/24**

Click **Review + Create**, then **Create**.

---

### 3. Create the Gateway Subnet

The VPN Gateway requires a dedicated subnet called **GatewaySubnet**.

Navigate to:

Virtual Network → Subnets → Add

Configuration:

- Subnet Name: **GatewaySubnet**
- Address Range: **10.1.255.0/27**

Click **Save**.

---

### 4. Create a Public IP Address

Navigate to:

Azure Portal → Public IP Addresses → Create

Configuration:

- Name: **VPNGateway-PublicIP**
- SKU: **Standard**
- Assignment: **Static**
- Region: **Canada Central**

Click **Review + Create**, then **Create**.

---

### 5. Deploy the VPN Gateway

Navigate to:

Azure Portal → Virtual Network Gateway → Create

Configuration:

- Name: **VPNGateway-Lab**
- Region: **Canada Central**
- Gateway Type: **VPN**
- VPN Type: **Route-Based**
- SKU: **VpnGw1**
- Generation: **Generation1**
- Virtual Network: **VNet-VPN-Lab**
- Public IP Address: **VPNGateway-PublicIP**

Click **Review + Create**, then **Create**.

Deployment typically takes **30–45 minutes**.

---

### 6. Configure Point-to-Site VPN

Navigate to:

VPN Gateway → Point-to-site configuration

Configuration:

- Address Pool: **172.16.0.0/24**
- Tunnel Type: **OpenVPN (SSL)**
- Authentication Type: **Azure Certificate**

Click **Save**.

---

### 7. Generate the VPN Client Configuration

Navigate to:

VPN Gateway → Point-to-site configuration

Click:

Download VPN Client

This downloads a configuration package containing:

- VPN client profile
- certificates
- connection configuration

---

### 8. Install the VPN Client

Install the **OpenVPN client** on the local machine.

Steps:

1. Extract the downloaded VPN client package
2. Locate the OpenVPN configuration file
3. Import the configuration profile into the VPN client

---

### 9. Establish VPN Connection

Open the VPN client and initiate the connection.

Once connected:

- The client receives an IP address from the **172.16.0.0/24 address pool**
- The machine becomes logically connected to the **Azure Virtual Network**

---

### 10. Verify Connectivity

Check the VPN adapter:

ipconfig
Test connectivity to internal resources: 

ping 10.1.1.4


Successful responses confirm that the VPN connection is functioning correctly.

---

## Screenshots



- Azure Virtual Network configuration
  <img width="1389" height="580" alt="image" src="https://github.com/user-attachments/assets/93642ece-c66b-44cb-a622-5e82911f7e0e" />

  <img width="1357" height="557" alt="image" src="https://github.com/user-attachments/assets/e01f9b28-dbf2-432f-85c7-627a46cabdd6" />

- VPN Gateway deployment
  <img width="1491" height="896" alt="image" src="https://github.com/user-attachments/assets/0a2cb699-c4ba-4876-8e68-5473ac3cc52e" />

- Point-to-Site configuration
  <img width="1470" height="727" alt="image" src="https://github.com/user-attachments/assets/48857666-62ee-4e92-a1df-6e52e13db895" />

- Successful VPN client connection
  <img width="1273" height="932" alt="image" src="https://github.com/user-attachments/assets/adb4f0c4-6dd5-4420-8025-06d90a5a635d" />

- Ping test results
  <img width="852" height="869" alt="image" src="https://github.com/user-attachments/assets/9800b8bf-f3d4-4574-8747-4a45fa82d3f8" />



---

## Project Outcome

This lab successfully demonstrates how to configure a **secure remote access solution using Azure Point-to-Site VPN**.

The implementation allows remote users to connect securely to private cloud infrastructure while keeping internal services protected from public internet exposure.

This setup reflects a common enterprise networking solution used in organizations that support remote work and hybrid cloud environments.

---

## Author

Huzaifa Zafar  
Cloud & IT Infrastructure Enthusiast

LinkedIn: https://www.linkedin.com/in/huzaifa-zafar-0b2375335
