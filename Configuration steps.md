
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
