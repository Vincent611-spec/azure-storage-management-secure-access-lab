# Azure Storage Management & Secure Access Lab

## Project Overview

This project was completed as part of my **Microsoft Azure Fundamentals (AZ-900)** learning journey and my continued development toward practical Azure administration skills.

The purpose of this lab was to gain hands-on experience with **Azure Storage** by building and configuring a storage environment for a fictional retail company called **CloudFirst Retail**.

Rather than only studying storage concepts theoretically, I used the Azure Portal to create and configure an Azure Storage Account, manage Blob data, explore storage access tiers, configure data protection features, implement lifecycle management, generate secure temporary access using a Shared Access Signature (SAS), review security settings, and explore Azure Storage redundancy options.

The project focused on four important areas of cloud storage administration:

- **Storage management**
- **Data protection**
- **Secure access**
- **Cost optimization**

This lab provided practical experience with how Azure administrators can store, protect, secure, and manage cloud data throughout its lifecycle.

---

# Why I Built This Project

Azure Storage is a core component of cloud infrastructure and is commonly used for application data, documents, backups, logs, media files, archives, and other forms of unstructured data.

As part of my Azure studies, I wanted to understand more than simply how to create a Storage Account.

I wanted to explore how an administrator would manage stored data after deployment, including:

- Organizing data using containers
- Protecting data from accidental deletion
- Recovering previous versions of files
- Managing frequently and infrequently accessed data
- Providing temporary access without exposing account credentials
- Applying secure communication settings
- Understanding storage redundancy
- Automating data lifecycle management

This project allowed me to practice these concepts directly in Azure while documenting the environment as part of my growing cloud portfolio.

---

# Business Scenario

**CloudFirst Retail** requires a cloud storage solution for inventory-related data.

The company needs a storage environment that can:

- Centrally store inventory files
- Prevent anonymous public access
- Support secure HTTPS communication
- Protect data against accidental deletion
- Preserve previous versions of modified files
- Provide temporary read-only access when required
- Automatically transition older data to lower-cost storage tiers
- Maintain redundant copies of stored data

To meet these requirements, I created and configured an Azure Storage environment and implemented several storage management, security, and data protection features.

---

# Objectives

The objectives of this project were to:

- Create and organize Azure resources using a Resource Group
- Deploy an Azure Storage Account
- Apply resource tags for organization
- Create a Blob Storage container
- Upload and manage Blob data
- Explore Azure Storage access tiers
- Configure Blob soft delete
- Configure container soft delete
- Enable Blob versioning
- Explore previous Blob versions and recovery
- Create a lifecycle management policy
- Generate a restricted Shared Access Signature (SAS)
- Test secure Blob access outside the Azure Portal
- Review Storage Account security settings
- Explore Azure Storage redundancy options
- Perform a final configuration review
- Document the environment using organized screenshots

---

# Technologies & Azure Services Used

- Microsoft Azure Portal
- Azure Resource Groups
- Azure Storage Accounts
- Azure Blob Storage
- Azure Storage Containers
- Azure Storage Access Tiers
- Azure Data Protection
- Azure Blob Versioning
- Azure Lifecycle Management
- Azure Shared Access Signatures (SAS)
- Azure Storage Redundancy
- Azure Resource Tags
- Microsoft Entra ID authentication within Azure Portal

---

# Skills Demonstrated

This project demonstrates practical experience with:

- Azure Portal navigation
- Azure resource organization
- Storage Account deployment
- Blob Storage administration
- Blob container management
- Cloud object storage
- Storage access tier management
- Blob soft delete
- Container soft delete
- Blob versioning
- Data recovery concepts
- Storage lifecycle management
- Shared Access Signatures (SAS)
- Time-limited access control
- Least-privilege access principles
- HTTPS-only access
- TLS security configuration
- Azure Storage redundancy concepts
- Cloud storage cost optimization
- Azure resource tagging
- Configuration verification
- Security-conscious documentation

---

# Project Architecture

The lab followed the following logical structure:

```text
Azure Subscription
│
└── Resource Group
    │
    └── Azure Storage Account
        │
        ├── Blob Storage
        │   │
        │   └── retail-data
        │       │
        │       └── retail-inventory.txt
        │
        ├── Data Protection
        │   ├── Blob Soft Delete
        │   ├── Container Soft Delete
        │   └── Blob Versioning
        │
        ├── Lifecycle Management
        │   ├── Transition to Cool Tier
        │   └── Transition to Archive Tier
        │
        ├── Secure Access
        │   └── Shared Access Signature (SAS)
        │
        └── Storage Redundancy
            └── Locally Redundant Storage (LRS)
```

---

# Project Structure

```text
azure-storage-management-secure-access-lab
│
├── README.md
│
└── Screenshots
    │
    ├── 01-resource-group
    ├── 02-storage-account
    ├── 03-blob-storage
    ├── 04-access-tiers
    ├── 05-sas-secure-access
    ├── 06-storage-security
    ├── 07-redundancy
    └── 08-storage-review
```

Screenshots are organized according to each stage of the project to make the implementation process easy to follow.

Sensitive information such as subscription identifiers, directory information, SAS tokens, and SAS URLs was excluded or redacted before documentation.

---

# Project Walkthrough

## Part 1 — Resource Group

Created a dedicated Azure Resource Group to logically organize the resources used throughout the project.

The Resource Group provided a management boundary for the lab and made it easier to organize, identify, and eventually remove project resources.

This reinforced the importance of using Resource Groups to structure Azure environments.

### Concepts Practiced

- Azure Resource Groups
- Subscription selection
- Azure regions
- Resource organization
- Naming conventions

---

## Part 2 — Azure Storage Account

Deployed an Azure Storage Account to provide the primary storage platform for the CloudFirst Retail environment.

The Storage Account was configured as a **StorageV2 (General Purpose v2)** account using **Standard performance**.

The environment included:

- StorageV2 account type
- Standard performance
- Hot default access tier
- Locally Redundant Storage (LRS)
- Secure transfer enabled
- Minimum TLS version 1.2
- Anonymous Blob access disabled

Resource tags were also used to improve organization and identify the purpose of the environment.

Example tags included:

```text
Environment: Development
Project: CloudFirst-Retail
```

This demonstrated how Azure Storage resources can be configured and organized as part of a structured cloud environment.

---

## Part 3 — Blob Storage

Created a Blob Storage container named:

```text
retail-data
```

The container was used to store sample inventory information for CloudFirst Retail.

A sample Blob named:

```text
retail-inventory.txt
```

was uploaded to the container.

The sample file contained fictional inventory information for products such as:

- Laptop
- Wireless Mouse
- Monitor

This exercise demonstrated the basic Azure Blob Storage hierarchy:

```text
Storage Account
      ↓
Container
      ↓
Blob
```

It also provided practical experience navigating Blob containers and managing stored objects through the Azure Portal.

---

## Part 4 — Azure Storage Access Tiers

Explored Azure Blob Storage access tiers to understand how organizations can balance data accessibility and storage cost.

### Hot Tier

Designed for data that is accessed frequently.

Typical examples include:

- Active application data
- Frequently accessed documents
- Current operational data

### Cool Tier

Designed for data that is accessed less frequently but still needs to remain readily available.

Typical examples include:

- Older business documents
- Infrequently accessed datasets
- Backup data

### Archive Tier

Designed for rarely accessed data intended for long-term retention.

Typical examples include:

- Historical records
- Long-term backups
- Compliance archives

This exercise demonstrated that storage architecture should consider both **how much data is stored** and **how frequently that data needs to be accessed**.

---

## Part 5 — Data Protection

Configured Azure Storage data protection features to reduce the risk of accidental data loss.

### Blob Soft Delete

Enabled Blob soft delete with a:

```text
7-day retention period
```

This allows deleted Blob data to remain recoverable during the configured retention period.

### Container Soft Delete

Enabled container soft delete with a:

```text
7-day retention period
```

This provides additional protection if an entire Blob container is accidentally deleted.

### Blob Versioning

Enabled Blob versioning to maintain previous versions of Blob objects when they are modified.

After modifying the sample inventory Blob, Azure maintained previous versions of the object.

I then explored the Blob version history and practiced restoring an earlier version by making it the current version.

This demonstrated how versioning can help protect data against:

- Accidental overwrites
- Unwanted changes
- User mistakes
- Application changes

---

## Part 6 — Lifecycle Management

Configured an Azure Storage lifecycle management policy for the `retail-data` container.

The lifecycle policy was designed to automatically transition Blob data to lower-cost storage tiers as the data becomes older and less frequently accessed.

The policy configured during the lab included:

```text
After 30 days
Hot → Cool

After 90 days
Cool → Archive
```

The lifecycle rule was scoped using the Blob prefix:

```text
retail-data/
```

This means the policy applies to Blob data stored within the `retail-data` container.

Lifecycle management demonstrated how Azure can automatically manage storage costs without requiring administrators to manually move individual files between access tiers.

---

# Storage Lifecycle Strategy

The storage lifecycle implemented in this lab can be represented as:

```text
New / Frequently Accessed Data
            │
            ▼
          HOT
            │
       After 30 Days
            │
            ▼
          COOL
            │
       After 90 Days
            │
            ▼
        ARCHIVE
```

This approach demonstrates how cloud storage can be optimized based on changing data access patterns.

---

## Part 7 — Secure Access with Shared Access Signature (SAS)

One of the key security exercises in the project involved creating a **Shared Access Signature (SAS)** for the `retail-inventory.txt` Blob.

A SAS allows temporary and restricted access to Azure Storage resources without sharing the Storage Account's primary access key.

The SAS used in the lab was configured with:

```text
Permission: Read
Protocol: HTTPS only
Access: Specific Blob
Duration: Limited
```

The generated SAS URL was then tested using a separate **Incognito browser session**.

The inventory Blob was successfully accessed without signing into the Azure Portal.

This demonstrated how SAS can be used to provide controlled external access to Azure Storage resources.

### Security Note

The actual:

- SAS token
- Full SAS URL
- Storage Account keys

were not included in the repository screenshots.

These values should be treated as credentials because anyone possessing a valid SAS URL may be able to access the resource according to the permissions granted by the token.

---

# Security Principles Applied

Several important security principles were reinforced during the project.

## Least Privilege

The SAS token was configured with only the permission required for the task:

```text
Read
```

Write, delete, and other unnecessary permissions were not granted.

---

## Limited Access Duration

The SAS was configured with a short validity period rather than providing indefinite access.

This reduces the amount of time the temporary credential remains usable.

---

## Secure Transport

The SAS was configured for:

```text
HTTPS only
```

The Storage Account also required secure transfer for REST API operations.

---

## TLS Security

The Storage Account used:

```text
Minimum TLS Version: 1.2
```

This helps ensure that supported client connections use modern transport security.

---

## Anonymous Access Disabled

Blob anonymous access was disabled.

This prevents unrestricted anonymous access to Blob data.

---

## Credential Protection

Sensitive information was excluded or redacted from the public documentation, including:

- Subscription ID
- SAS tokens
- SAS URLs
- Storage Account keys
- Directory/account information where appropriate

This was an important part of documenting the project securely.

---

## Part 8 — Azure Storage Redundancy

Explored Azure Storage redundancy options to understand how Azure protects data from infrastructure failures.

The redundancy options reviewed included:

### Locally Redundant Storage (LRS)

Maintains multiple copies of data within a single Azure datacenter in the primary region.

### Zone-Redundant Storage (ZRS)

Replicates data across multiple availability zones within the primary Azure region.

### Geo-Redundant Storage (GRS)

Replicates data to a secondary geographic Azure region in addition to maintaining copies in the primary region.

### Read-Access Geo-Redundant Storage (RA-GRS)

Provides geo-replication while also allowing read access to the secondary region.

The Storage Account used for this lab was configured with:

```text
Locally Redundant Storage (LRS)
```

This exercise reinforced that redundancy selection depends on factors such as:

- Cost
- Availability requirements
- Business continuity
- Disaster recovery requirements
- Geographic resilience

---

## Part 9 — Final Storage Configuration Review

Performed a final review of the Storage Account to verify the configuration implemented throughout the project.

The final environment included:

| Configuration | Status |
|---|---|
| Account Type | StorageV2 |
| Performance | Standard |
| Default Access Tier | Hot |
| Redundancy | LRS |
| Secure Transfer | Enabled |
| Minimum TLS | 1.2 |
| Anonymous Blob Access | Disabled |
| Blob Soft Delete | Enabled — 7 Days |
| Container Soft Delete | Enabled — 7 Days |
| Blob Versioning | Enabled |
| Lifecycle Management | Configured |
| SAS Access | Successfully Tested |

This final review helped connect the individual exercises into one complete Azure Storage management scenario.

---

# Screenshots

The repository contains screenshots documenting the major stages of the project.

## 01 — Resource Group

Documents the Azure Resource Group used to organize the project resources.

---

## 02 — Storage Account

Documents Storage Account deployment and configuration.

---

## 03 — Blob Storage

Documents:

- Blob container creation
- Blob upload
- Sample inventory data
- Data protection
- Blob versioning
- Lifecycle management

---

## 04 — Access Tiers

Documents the exploration and configuration of Azure Blob Storage access tiers.

---

## 05 — SAS Secure Access

Documents the successful test of temporary read-only Blob access using a Shared Access Signature.

Sensitive SAS credentials were intentionally excluded from the screenshots.

---

## 06 — Storage Security

Documents Storage Account security and data protection configuration.

---

## 07 — Redundancy

Documents the Storage Account redundancy configuration and available redundancy options.

---

## 08 — Storage Review

Documents the final Storage Account configuration and project review.

---

# Key Security Takeaways

This project reinforced that cloud storage security involves more than simply storing files.

A properly managed storage environment should consider:

- Who can access the data
- What permissions users require
- How long access should remain valid
- Whether anonymous access should be permitted
- How data is protected during transmission
- How deleted data can be recovered
- How overwritten data can be restored
- How credentials are protected
- How data is replicated
- How storage configuration is verified

The SAS exercise was particularly valuable because it demonstrated the difference between providing **controlled access to a specific resource** and exposing broader Storage Account credentials.

---

# Cost Optimization Takeaways

Azure Storage costs are influenced by several factors, including:

- Amount of data stored
- Storage access tier
- Data access frequency
- Retrieval operations
- Redundancy configuration
- Data retention
- Lifecycle management policies

Lifecycle management provides a practical method for automatically optimizing storage costs as data becomes less frequently accessed.

For example:

```text
Frequently Accessed
        │
        ▼
       Hot
        │
        ▼
Less Frequently Accessed
        │
        ▼
       Cool
        │
        ▼
Long-Term / Rarely Accessed
        │
        ▼
     Archive
```

This demonstrated that effective cloud cost management involves matching the storage configuration to the actual data access pattern.

---

# What I Learned

This project significantly improved my understanding of Azure Storage administration.

I gained practical experience with:

- Deploying Azure Storage Accounts
- Creating Blob containers
- Uploading and managing Blob data
- Understanding Azure Storage access tiers
- Configuring Blob soft delete
- Configuring container soft delete
- Enabling Blob versioning
- Exploring previous Blob versions
- Recovering previous versions of data
- Creating lifecycle management policies
- Using Blob prefixes to scope lifecycle rules
- Creating temporary SAS access
- Applying read-only permissions
- Using HTTPS-only access
- Testing SAS access outside the Azure Portal
- Reviewing Storage Account security settings
- Understanding Azure Storage redundancy
- Organizing resources using tags
- Protecting sensitive information in technical documentation

Most importantly, I developed a clearer understanding of how **storage management, security, data protection, availability, cost optimization, and access control work together within an Azure Storage environment**.

---

# Challenges & Troubleshooting

Throughout the lab, I encountered situations where Azure Portal settings and workflows required additional investigation and verification.

Working through these situations helped improve my ability to:

- Navigate Azure Storage settings
- Locate configuration options
- Understand Blob version behavior
- Verify configuration changes
- Interpret Azure Portal settings
- Test resource access independently
- Review configurations before applying changes
- Troubleshoot cloud resources systematically

This reinforced an important lesson:

> Cloud administration is not only about knowing where a setting is located. It is also about understanding what the setting changes, why it is being configured, and how to verify that the configuration works as expected.

---

# Real-World Relevance

The concepts practiced in this project are relevant to responsibilities commonly encountered in cloud administration, infrastructure, and IT environments.

Cloud administrators may need to:

- Provision Storage Accounts
- Organize cloud resources
- Manage access to stored data
- Protect data from accidental deletion
- Maintain previous versions of files
- Control public exposure
- Generate temporary access
- Enforce secure communication
- Optimize storage costs
- Configure data lifecycle policies
- Evaluate redundancy requirements
- Review resource security
- Document infrastructure changes

This project provided practical exposure to these responsibilities within a controlled Azure learning environment.

---

# Future Improvements

Future improvements to this project could include:

- Implementing Azure RBAC for more granular Storage access
- Exploring Microsoft Entra ID-based Blob authorization
- Creating a User Delegation SAS
- Disabling unrestricted public network access
- Configuring Storage Account firewall rules
- Restricting access to selected networks
- Implementing Virtual Network service endpoints
- Implementing Azure Private Endpoints
- Exploring customer-managed encryption keys
- Configuring Azure Storage diagnostic settings
- Sending Storage logs to Azure Monitor
- Creating alerts for Storage Account activity
- Using Azure CLI to deploy and configure storage resources
- Rebuilding the environment using Infrastructure as Code
- Exploring Azure Bicep
- Comparing LRS, ZRS, GRS, RA-GRS, GZRS, and RA-GZRS
- Testing more advanced Blob recovery scenarios

These improvements would build on the fundamentals practiced in this project and introduce concepts that are increasingly relevant when progressing toward **Microsoft Azure Administrator (AZ-104)**.

---

# Project Outcome

By completing this project, I moved beyond simply learning Azure Storage terminology and gained hands-on experience configuring an Azure Storage environment.

The completed lab demonstrated:

**Resource Organization → Storage Deployment → Blob Management → Data Protection → Lifecycle Management → Secure Access → Security Review → Redundancy**

This project strengthened my understanding of how Azure Storage can be configured to provide a balance between:

**Security + Availability + Recoverability + Accessibility + Cost Efficiency**

---

## Author

**Vincent Ekekwe**

Aspiring Cloud Administrator | IT Support Engineer

**Microsoft Azure: AZ-900 → AZ-104**