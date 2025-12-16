# Azure-SecureStorage-Implementation-Project

This project demonstrates the configuration of a secure, cost-optimized, and access-controlled Azure Storage solution. The setup replicates real-world enterprise policies, ensuring:

No public network access

Blob immutability

Lifecycle management for cost savings

Fine-grained access via Shared Access Signatures (SAS)

Integration with Virtual Networks (VNets) and Service Endpoints

🖼️ **Step-by-Step Walkthrough**

**Storage Account Created**

An Azure Storage account was created in Canada Central with geo-redundant storage (Canada Central + Canada East).

<img width="1470" height="831" alt="Screenshot 2025-12-15 at 7 06 15 PM" src="https://github.com/user-attachments/assets/2986613b-1eb2-457f-b043-2fc87e4408c5" />



**Public Network Access Disabled**

Ensured secure access by disabling all public network access.


<img width="1470" height="831" alt="Screenshot 2025-12-15 at 7 06 34 PM" src="https://github.com/user-attachments/assets/3c50f282-d9d5-410c-b9a1-7ed43491842c" />


**Soft-Delete & Retention Enabled**

Enabled soft-delete (self-delete) to prevent accidental data loss.


<img width="1469" height="793" alt="Screenshot 2025-12-15 at 7 07 46 PM" src="https://github.com/user-attachments/assets/f715285e-6a83-4285-8e35-e710f9bfb24e" />


**Selected Network Access Enabled**

Access was limited to specific networks (virtual networks or trusted machine IPs).


<img width="1469" height="758" alt="Screenshot 2025-12-15 at 7 13 03 PM" src="https://github.com/user-attachments/assets/e7f144e5-a7af-4cec-b6a1-78711489d016" />


**Geo-Redundancy Configured**

Redundancy ensures high availability across regions.


<img width="1467" height="814" alt="Screenshot 2025-12-15 at 7 14 24 PM" src="https://github.com/user-attachments/assets/a683d36a-9d82-4dca-84cf-aecaf1c4adb1" />



**Lifecycle Rule: MoveToCool**

Applied to all blobs.

<img width="1466" height="765" alt="Screenshot 2025-12-15 at 7 16 42 PM" src="https://github.com/user-attachments/assets/7ad9c9af-bcf1-4675-9b54-80471800f776" />


**Rule: If not modified in 30+ days → automatically moved to Cool tier to reduce storage costs.**

<img width="1467" height="766" alt="Screenshot 2025-12-15 at 7 17 42 PM" src="https://github.com/user-attachments/assets/b467d044-5e90-40d6-b1ec-753bd59de7ff" />


**Created container container1.**

<img width="1468" height="831" alt="Screenshot 2025-12-15 at 7 43 22 PM" src="https://github.com/user-attachments/assets/93cf4ae8-4fdb-4b45-827e-89ec51a68043" />


**Uploaded blob file.**

<img width="1466" height="833" alt="Screenshot 2025-12-15 at 7 55 42 PM" src="https://github.com/user-attachments/assets/86a7f0ed-0574-4d30-a490-45f2fb496b40" />


**Applied Time-Based Retention Policy (180 days) to ensure compliance and prevent tampering.**

<img width="1466" height="832" alt="Screenshot 2025-12-15 at 7 46 31 PM" src="https://github.com/user-attachments/assets/07397b71-db78-4bb9-91c6-cbe4949bb54f" />


**Access Attempt in Incognito Browser (Failed)**

Verified that direct blob access fails due to private access restrictions.


<img width="1470" height="876" alt="Screenshot 2025-12-15 at 7 58 22 PM" src="https://github.com/user-attachments/assets/258e01cb-b123-4723-a17b-4f48fed5c943" />


**Shared Access Signature (SAS) Applied**

Generated a SAS key with limited duration (e.g., 2 days).

<img width="1467" height="833" alt="Screenshot 2025-12-15 at 8 02 07 PM" src="https://github.com/user-attachments/assets/b451f041-1ab3-4aed-acea-5286cfa2b39c" />


Re-tested access → blob successfully read via SAS in incognito.

<img width="1467" height="876" alt="Screenshot 2025-12-15 at 8 03 10 PM" src="https://github.com/user-attachments/assets/264f6999-dd3b-42b1-84d4-908fce74c0e1" />


**Azure File Share Configured**

Created and uploaded files to an Azure File Share.

<img width="1469" height="828" alt="Screenshot 2025-12-15 at 8 06 17 PM" src="https://github.com/user-attachments/assets/48e4629b-e39b-47b5-b4a7-eb002fe10bdf" />


Validated structure and access via Storage Explorer.



**Virtual Network Setup + Service Endpoint**

Created a Virtual Network.

<img width="1468" height="769" alt="Screenshot 2025-12-15 at 8 29 23 PM" src="https://github.com/user-attachments/assets/a3ce73a5-7ce6-4b49-ac8f-0c173cd8cd68" />


**Added Service Endpoint for Microsoft.Storage to default subnet.**

<img width="1470" height="813" alt="Screenshot 2025-12-15 at 8 33 07 PM" src="https://github.com/user-attachments/assets/a23dac6b-c261-4f44-a2cb-62a6eb85c67e" />


**Restrict Storage Access to VNet Only**

Added only vnet1 to the storage account's selected networks.

Removed machine IP, confirming that only VMs in vnet1 can access storage.


**Final test: local machine blocked from blob/file access.**

<img width="1470" height="831" alt="Screenshot 2025-12-15 at 8 42 12 PM" src="https://github.com/user-attachments/assets/f2250869-17bf-4d91-98a5-f41a438d1d50" />


<img width="1470" height="832" alt="Screenshot 2025-12-15 at 8 43 08 PM" src="https://github.com/user-attachments/assets/4addfba1-ee57-41a2-9c89-00c1b63088db" />


**🔒 Security Highlights**

100% private blob access (no anonymous/public access)

VNet + Service Endpoint enforced network isolation

Immutability policy and soft delete enabled

SAS tokens provide temporary, scoped access


**💡 Skills Demonstrated**

Azure Blob and File storage configuration

Lifecycle Management Rules

Immutable Blob Policies

Shared Access Signature (SAS) tokens

Virtual Network and Service Endpoint setup

Network security hardening
