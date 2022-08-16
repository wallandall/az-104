# Azure Storage Accounts

Azure Storage accounts are the top level resource for the Azure Storage Service and containes all Azure Storage data object i.e.:

- Azure Blob: Object oriented storage solution e.ge virtual hard disks, images and videos
- Azure Queue: Message based storagefor microservice
- Azure Files: Cloud based file sharing service
- Azure Table: Non-relational, semi-strucutred data storage service

Storage Accounts consist of :

- Account Type determines the features and costs.
- Replication: Determines infrastrucutre redundancy.
- Performance Tier: Determines the performance levels.
- Access Tier: Determines the access levels and data costs.

## Conceptualizing Azure Blob Storage

Azure Blob storage is Microsoft's object storage solution for the cloud. Blob storage is optimized for storing massive amounts of unstructured data such as text or binary data and is designed for :

- Serving images or documents directly to a browser.
- Storing files for distributed access.
- Streaming video and audio.
- Writing to log files.
- Storing data for backup and restore, disaster recovery, and archiving.
- Storing data for analysis by an on-premises or Azure-hosted service.

Components of Blob Storage Architecture:

- Storage Account
- Blob Container: A container organizes a set of blobs, similar to a directory in a file system. A storage account can include an unlimited number of containers, and a container can store an unlimited number of blobs.
- Blobs: The data that is stored in the containers. Azure supports three types of blobs:
  - Block Blobs: store text and binary data. Block blobs are made up of blocks of data that can be managed individually. Block blobs can store up to about 190.7 TiB.
  - Append Blobs: are made up of blocks like block blobs, but are optimized for append operations. Append blobs are ideal for scenarios such as logging data from virtual machines.
  - Page Blobs: store random access files up to 8 TiB in size. Page blobs store virtual hard drive (VHD) files and serve as disks for Azure virtual machines.


## Configuring Blob Object Replication

Object replication asynchronously copies block blobs between a source storage account and a destination account. Some scenarios supported by object replication include:

- Minimizing latency. Object replication can reduce latency for read requests by enabling clients to consume data from a region that is in closer physical proximity.
- Increase efficiency for compute workloads. With object replication, compute workloads can process the same sets of block blobs in different regions.
- Optimizing data distribution. You can process or analyze data in a single location and then replicate just the results to additional regions.
- Optimizing costs. After your data has been replicated, you can reduce costs by moving it to the archive tier using life cycle management policies.

## Configure Blob Lifecycle Management

Blob Lifecycle Management is a feature of the blob service that enables autiomation to manage the lifecycle of blobs, by moving blobs between access tiers to optimise storage costs.

Azure Storage access tiers include:

- Hot tier - An online tier optimized for storing data that is accessed or modified frequently. The Hot tier has the highest storage costs, but the lowest access costs.
- Cool tier - An online tier optimized for storing data that is infrequently accessed or modified. Data in the Cool tier should be stored for a minimum of 30 days. The Cool tier has lower storage costs and higher access costs compared to the Hot tier.
- Archive tier - An offline tier optimized for storing data that is rarely accessed, and that has flexible latency requirements, on the order of hours. Data in the Archive tier should be stored for a minimum of 180 days.

More information on Lifecycle Policies can be found [here](https://docs.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview)

## Configuring Azure Files

Azure Files offers fully managed file shares in the cloud that are accessible via the industry standard Server Message Block (SMB) protocol, Network File System (NFS) protocol, and Azure Files REST API. Azure file shares can be mounted concurrently by cloud or on-premises deployments. SMB Azure file shares are accessible from Windows, Linux, and macOS clients. NFS Azure file shares are accessible from Linux or macOS clients. Additionally, SMB Azure file shares can be cached on Windows servers with Azure File Sync for fast access near where the data is being used.

More information can be found [here](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-introduction)



[Back](ReadMe.md)
