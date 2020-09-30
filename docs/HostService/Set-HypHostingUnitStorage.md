
# Set-Hyphostingunitstorage
Sets options for a storage location on a hosting unit.
## Syntax
```
Set-HypHostingUnitStorage [-LiteralPath] <String> [-StoragePath] <String> [-StorageType <StorageType>] [-Superseded <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to set options for storage locations that are defined for a hosting unit. Do not use this command if the connection for the hosting unit is in maintenance mode.


## Related Commands

* [New-Item](../New-Item/)
* [Add-HypMetadata](../Add-HypMetadata/)
* [Remove-HypHostingUnitStorage](../Remove-HypHostingUnitStorage/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path to the hosting unit which defines the storage. The path must be in one of the following formats: &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt; or  &lt;drive&gt;:\\HostingUnits\\{&lt;HostingUnit Uid&gt;} | true | false |  |
| StoragePath | Specifies the path to the storage that will be modified. The path must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;ConnectionName&gt;\\MyStorage.storage or  &lt;drive&gt;:\\Connections\\{&lt;Connection Uid&gt;}\\MyStorage.storage or  &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt;\\MyStorage.storage or  &lt;drive&gt;:\\HostingUnits\\{&lt;hostingUnit Uid&gt;}\\MyStorage.storage | true | true (ByValue) |  |
| StorageType | Specifies the type of storage in StoragePath. Supported storage types are: OSStorage PersonalvDiskStorage TemporaryStorage | false | false | OSStorage |
| Superseded | Specifies that this storage has been superseded and must not be used for future provisioning operations. Existing virtual machines using this storage will continue to function. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects. This can be a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String<br>    You Can Pipe A String That Contains A Path To Add-Hyphostingunitstorage (Storagepath Parameter).

## Return Values

### Citrix.Xdpowershell.Hostingunit<br>    Set-Hyphostingunitstorage Returns An Object Containing The New Definition Of The Hosting Unit.<br>    Hostingunituid &lt;Guid&gt;<br>        Specifies The Unique Identifier For The Hosting Unit.<br>    Hostingunitname &lt;String&gt;<br>        Specifies The Name Of The Hosting Unit.<br>    Hypervisorconnection &lt;Citrix.Xdpowershell.Hypervisorconnection&gt;<br>        Specifies The Connection That The Hosting Unit Uses To Access A Hypervisor.<br>    Rootid &lt;String&gt;<br>        Identifies, To The Hypervisor, The Root Of The Hosting Unit.<br>    Rootpath &lt;String&gt;<br>        The Hosting Unit Provider Path That Represents The Root Of The Hosting Unit.<br>    Storage &lt;Citrix.Xdpowershell.Storage\[\]&gt;<br>        The List Of Storage Items That The Hosting Unit Can Use.<br>    Personalvdiskstorage &lt;Citrix.Xdpowershell.Storage\[\]&gt;<br>        The List Of Storage Items That The Hosting Unit Can Use For Storing Personal Data.<br>    Vmtaggingenabled &lt;Boolean&gt;<br>        Specifies Whether Or Not The Metadata In The Hypervisor Can Be Used To Store Information About The Xendesktop Machine Creation Service.<br>    Networkid &lt;String&gt;<br>        The Hypervisor's Internal Identifier That Represents The Network Specified For The Hosting Unit.<br>    Networkpath &lt;String&gt;<br>        The Hosting Unit Provider Path To The Network Specified For The Hosting Unit.<br>    Additionalstorage<br>        The List Of Additional Storage Items That The Hosting Unit Can Use.<br>    Metadata &lt;Citrix.Xdpowershell.Metadata\[\]&gt;<br>        A List Of Key Value Pairs That Can Store Additional Information About The Hosting Unit.

## Notes
The storage path must be valid for the hosting unit. The rules that are applied are as follows: XenServer (HypervisorConnection Type = XenServer)<br>    NA<br>    VMWare vSphere/ESX (HypervisorConnection Type = vCenter)<br>    The storage path must be directly contained in the root path item of the hosting unit.<br>    Microsoft SCVMM/Hyper-v (HypervisorConnection Type = SCVMM)<br>    Only one storage entry for these connection types is valid, and it must reference an SMB share. Additionally, if a Hyper-V failover cluster is used the SMB share must be the top-level mount point of the cluster shared volume on one of the servers in the cluster (i.e. C:\\ClusterStorage).<br>    In the case of failure, the following errors can be produced.<br>    Error Codes<br>    -----------<br>    HostingUnitsPathInvalid<br>    The path provided is not to an item in a subdirectory of a hosting unit item.<br>    HostingUnitStoragePathInvalid<br>    The specified path is invalid.<br>    HostingUnitStoragePathInvalid<br>    The storage path cannot be found or is invalid. See notes above about validity.<br>    HostingUnitStorageDuplicateObjectExists<br>    The specified storage path is already part of the hosting unit.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Set-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage' -Superseded $true

          HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457

          HostingUnitName      : MyHostingUnit

          HypervisorConnection : MyConnection

          RootPath             : /

          RootId               :

          NetworkPath          : /Network 0.network

          NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1

          Storage              : {/Local storage.storage, /newStorage.storage}

          PersonalvDiskStorage : {/newStorage.storage}

          VMTaggingEnabled     : True

          AdditionalStorage    : {TemporaryStorage}

          Metadata             : {}
```
#### Description
The command updates a storage location called "newStorage.storage" associated with the hosting unit called "MyHostingUnit".
