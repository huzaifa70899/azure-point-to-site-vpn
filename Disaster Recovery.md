# Azure File Share Backup & Disaster Recovery

This project demonstrates how to implement **disaster recovery** for Azure File Share using Azure Backup in a secure Point-to-Site VPN environment.

---

## Overview

Remote employees need secure access to internal file storage without risking data loss.  
This setup ensures that any accidental deletion or corruption of files can be quickly recovered using Azure Backup policies.

- Secure access via **Point-to-Site VPN**
- Azure File Share as centralized storage
- Azure Backup to protect against accidental deletion or disasters

---

## Real-World Scenario

A company hosts sensitive files in Azure, accessible only through a private network.  
To prevent data loss:

- Daily backups are scheduled
- Retention policies maintain previous versions
- File restoration is tested periodically

This guarantees **business continuity** for remote employees.

---

## Technologies Used

- Microsoft Azure
- Azure File Share
- Azure Backup & Recovery
- Point-to-Site VPN
- Network Security Groups (NSG)
- Azure Portal

---

## Configuration Steps

### 1. Configure Azure File Share
1. Navigate to the storage account in Azure Portal.
2. Create a new **File Share** within the VNet.
3. Set access permissions for internal VMs via VPN only.

### 2. Enable Backup for File Share
1. In Azure Portal, go to **Backup Center**.
2. Select the file share as a backup item.
3. Configure **backup policy**:
   - Frequency: Daily
   - Retention: 30 days

### 3. Test Disaster Recovery
1. Delete a file from the File Share.
2. Initiate a restore from the backup.
3. Verify that the file is successfully recovered.

### 4. Security Considerations
- NSG rules ensure the file share is accessible **only through VPN**.
- Backup data is encrypted and stored securely within Azure.

---

## Outcome

- Remote users can safely access file storage over the VPN.  
- All files are protected against accidental deletion.  
- Azure Backup provides **quick recovery** to minimize downtime.  
- Demonstrates enterprise-ready **disaster recovery practices** in the cloud.

---

## Author

**Huzaifa Zafar**  
Cloud & IT Infrastructure Enthusiast  

[LinkedIn Profile](https://www.linkedin.com/in/huzaifa-zafar-0b2375335)
