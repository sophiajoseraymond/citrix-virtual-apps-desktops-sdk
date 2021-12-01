
# about\_ProvCustomProperties

## Topic
Citrix Machine Creation Service SDK - Custom Properties


## Short Description
Overview of custom properties settings of the provisioning scheme.


## Long Description
Custom properties are the properties of the provisioning scheme that are specific to the target hosting infrastructure. Custom properties can be used to control or tune behaviors of the provisioning scheme.


## Custom Properties For Azure
The following custom properties are specific to hosting infrastructure targets using the AzureRM plugin


* StorageAccountType: Storage account type used for provisioned virtual machine disks. Storage account types include: Standard\_LRS, StandardSSD\_LRS and Premium\_LRS. If this property is not specified, Standard\_LRS is used by default.
* IdentityDiskStorageType: Storage type used for the provisioned virtual machine identity disk. If this property is not specified, StandardSSD\_LRS is used by default.
* WBCDiskStorageType: Storage type for the provisioned virtual machine write back cache disk. This property only applies to a provisioning scheme with UseWriteBackCache enabled. If this property is not specified, the value specified in the StorageAccountType property is used for WBCDiskStorageType.
* ResourceGroups: Resource groups used to contain provisioned virtual machines. If this property is not specified, Citrix managed resource groups are created.
* LicenseType: The Windows license type used for provisioned virtual machines. Options include Windows\_Server, Windows\_Client and empty. A Windows license fee is charged by Azure if value is empty. When Windows\_Server or Windows\_Client is used, it means customer has a valid license.
* OsType: Operating system type used for the provisioned virtual machine. OS types include either Windows or Linux. If an OS type is not specified, Windows is used by default.
* UseManagedDisks: Indicate whether to use Azure managed disks for the provisioned virtual machine. Specify either True or False. If this property is not specified, UseManagedDisks is set to True by default.
* PersistWBC: Persist the write back cache disk for the non-persistent provisioned virtual machine between power cycles. Specify either True or False. This property only applies to a provisioning scheme with UseWriteBackCache enabled. If this property is not specified, the write back cache disk is deleted when the virtual machine is shut down, and is re-created when the virtual machine is powered on.
* PersistOsDisk: Persist the OS disk when power cycling the non-persistent provisioned virtual machine. Specify either True or False. This property only applies to a provisioning scheme with UseWriteBackCache enabled. If this property is not specified, the OS disk is deleted when the virtual machine is shut down, and is re-created when the virtual machine is powered on.
* PersistVm: Persist the non-persistent provisioned virtual machine in Azure environments when power cycling. Specify either True or False. This property only applies when the PersistOsDisk property is set to True. If this property is not specified, they will be deleted from Azure when powered off.
* MachinesPerStorageAccount: The maximum number of virtual machines containing unmanged disks that can be provisioned under a single Azure storage account. This property only applies when the UseManagedDisks property is set to False. If this property is not specified, 40 virtual machines is used by default.
* StorageAccountsPerResourceGroup: The maximum number of Azure storage accounts provisioned under a single Azure resource group. This property only applies when the UseManagedDisks property is set to False. If this property is not specified, 100000 storage accounts per resource group is used by default.
* DiskEncryptionSetId: The Azure Encryption Set ID that references the customer-managed encryption used for the server-side encryption key to encrypt disks for provisioned virtual machines. The supplied value must be a valid Azure resource ID. This property only applies when the UseManagedDisks property is set to True. If this property is not specified, Citrix takes no action on the provisioned virtual machines. Virtual machine disks use Azure storage encryption for data at rest.
* UseSharedImageGallery: Use Azure Shared Image Gallery as a published image repository for MCS to provision virtual machines in Azure. Specify either True or False. This property only applies when the UseManagedDisks property is set to True. If this property is not specified, UseSharedImageGallery is set to False by default, and the prepared images for the machine catalog are stored as managed disk snapshots.
* SharedImageGalleryReplicaRatio: The ratio of virtual machines to shared image gallery version replicas. This value is an integer greater than 0. This property only applies when the UseSharedImageGallery property is set to True. If this property is not specified, SharedImageGalleryReplicaRatio is set to 1000 for persistent OS disks and 40 for non-persistent OS disks by default.
* SharedImageGalleryReplicaMaximum: The maximum number of replicas for each shared image gallery version. This value is an integer greater than
  0.  
This property only applies when the UseSharedImageGallery property is set to True. If this property is not specified, SharedImageGalleryReplicaMaximum is set to 10 by default.

* DedicatedHostGroupId: The Azure Dedicated Host Group ID. Format the value as "myResourceGroup/myHostGroup". If this property is used, virtual machines are provisioned on the Azure dedicated hosts specified by DedicatedHostGroupId.
* Zones: The Azure Availability Zones containing provisioned virtual machines. Use a comma as a delimiter for multiple zones. If this property is not specified, the provisioned virtual machine is randomly placed across all Azure Availability Zones in the region defined by the hosting unit.
* UseEphemeralOsDisk: Use Azure Ephemeral OS disk for the provisioned virtual machine. Specify either True or False. This property only applies when the UseManagedDisks property is not False and the UseSharedImageGallery property is set to True. When the UseEphemeralOsDisk property is set to True, the chosen virtual machine size supports the size of the Ephemeral OS disk and the cache disk, which is larger than the master image disk. If this property is not specified, UseEphemeralOsDisk is set to False by default.

## Custom Properties For Aws

The following custom properties are specific to hosting infrastructure targets to using the AWS plugin.


* AwsCaptureInstanceProperties: Capture AWS instance properties, including the Identity Access Management role and tags from the master image, then apply them to the provisioned virtual machines. Specify either True or False. If this property is not specified, AwsCaptureInstanceProperties is set to False by default.
* AwsOperationalResourcesTagging: Apply tags from master image to all Citrix created operational resources including virtual machines, VM disks, VM network interfaces, S3 buckets, S3 objects, launch templates and AMIs. Specify either True or False. When setting this property to True, you must also set the AwsCaptureInstanceProperties parameter to True. If this value is not specified, the AwsOperationalResourcesTagging paramter is set to False by default.

## Custom Properties For Gcp

The following custom properties are specific to hosting infrastructure targets to using the GCP plugin.


* CatalogZones: GCP zones to place provisioned virtual machines. Use comma as delimiter for multiple zones. If this property is not specified, the provisioned virtual machine is randomly placed across GCP zones.
* CryptoKeyId: Use the customer-managed encryption key to encrypt data on provisioned virtual machines. Format the value as "project:location:keyRing:key". If this property is not specified, a system managed encryption key is used.

## See Also

* [New-ProvScheme](../New-ProvScheme/)
* [Set-ProvScheme](../Set-ProvScheme/)

