
# Remove-Hyphostingunitstorage
Removes storage from a hosting unit.
## Syntax
```
Remove-HypHostingUnitStorage [-LiteralPath] <String> [-StoragePath <String>] [-StorageType <StorageType>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to remove storage locations from a hosting unit. This does not remove the storage from the hypervisor, only the reference to the storage for the Host Service. After removal, the storage is no longer used to store hard disks (when creating new virtual machines with the Machine Creation Service). The hard disks located already on the storage remain in place and virtual machines that have been created already continue to use the storage until they are removed from the deployment. Do not use this command if the connection for the hosting unit is in maintenance mode. If the storage location to be removed no longer exists on the hypervisor for the hosting unit, you must supply a fully qualified path to the storage location.


## Related Commands

* [Add-HypHostingUnitStorage](../Add-HypHostingUnitStorage/)
* [Set-HypHostingUnitStorage](../Set-HypHostingUnitStorage/)
* [New-Item](../New-Item/)
* [Add-HypMetadata](../Add-HypMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path to the hosting unit which defines the storage. The path must be in one of the following formats: &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt; or  &lt;drive&gt;:\\HostingUnits\\{&lt;HostingUnit Uid&gt;} | true | false |  |
| StoragePath | Specifies the path in the hosting unit provider of the storage to remove. If StoragePath is not specified, all storage is removed from the hosting unit. The path must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;ConnectionName&gt;\\MyStorage.storage or  &lt;drive&gt;:\\Connections\\{&lt;Connection Uid&gt;}\\MyStorage.storage or  &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt;\\MyStorage.storage or  &lt;drive&gt;:\\HostingUnits\\{&lt;hostingUnit Uid&gt;}\\MyStorage.storage | false | true (ByValue) |  |
| StorageType | Specifies the type of storage in StoragePath. Supported storage types are: OSStorage PersonalvDiskStorage TemporaryStorage | false | false | OSStorage |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. This can be a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String<br>    You Can Pipe A String That Contains A Path To Remove-Hyphostingunitstorage (Storagepath Parameter).

## Return Values

### Citrix.Xdpowershell.Hostingunit<br>    Remove-Hyphostingunitstorage Returns An Object Containing The New Definition Of The Hosting Unit.<br>    Hostingunituid &lt;Guid&gt;<br>        Specifies The Unique Identifier For The Hosting Unit.<br>    Hostingunitname &lt;String&gt;<br>        Specifies The Name Of The Hosting Unit.<br>    Hypervisorconnection &lt;Citrix.Xdpowershell.Hypervisorconnection&gt;<br>        Specifies The Connection That The Hosting Unit Uses To Access A Hypervisor.<br>    Rootid &lt;String&gt;<br>        Identifies, To The Hypervisor, The Root Of The Hosting Unit.<br>    Rootpath &lt;String&gt;<br>        The Hosting Unit Provider Path That Represents The Root Of The Hosting Unit.<br>    Storage &lt;Citrix.Xdpowershell.Storage\[\]&gt;<br>        The List Of Storage Items That The Hosting Unit Can Use.<br>    Personalvdiskstorage &lt;Citrix.Xdpowershell.Storage\[\]&gt;<br>        The List Of Storage Items That The Hosting Unit Can Use For Storing Personal Data.<br>    Vmtaggingenabled &lt;Boolean&gt;<br>        Specifies Whether Or Not The Metadata In The Hypervisor Can Be Used To Store Information About The Xendesktop Machine Creation Service.<br>    Networkid &lt;String&gt;<br>        The Hypervisor's Internal Identifier That Represents The Network Specified For The Hosting Unit.<br>    Networkpath &lt;String&gt;<br>        The Hosting Unit Provider Path To The Network Specified For The Hosting Unit.<br>    Additionalstorage<br>        The List Of Additional Storage Items That The Hosting Unit Can Use.<br>    Metadata &lt;Citrix.Xdpowershell.Metadata\[\]&gt;<br>        A List Of Key Value Pairs That Can Store Additional Information About The Hosting Unit.

## Notes
After storage is removed, it is the administrator's responsibility to maintain its contents. The Citrix XenDesktop Machine Creation Service does not attempt to clean up any data that is stored in the storage location.<br>    If all storage is removed from the hosting unit, other features of the Machine Creation Service stops functioning until some storage is added again.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    HostingUnitsPathInvalid<br>    The path provided is not to an item in a subdirectory of a hosting unit item.<br>    HostingUnitStorageObjectToDeleteDoesNotExist<br>    The storage path specified is not part of the hosting unit.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Remove-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage'
```
#### Description
The command removes the OS storage location called "newStorage.storage" from the hosting unit called "MyHostingUnit"
### Example 2
```
c:\PS>Get-ChildItem XDHYP:\HostingUnits\Host\\*.storage | Remove-HypHostingUnitStorage XDHYP:\HostingUnits\Host1
```
#### Description
The command removes all OS storage from all hosting units called "Host1".
### Example 3
```
c:\PS>Get-ChildItem XDHYP:\HostingUnits\Host\\*.storage | Remove-HypHostingUnitStorage -StorageType PersonalvDiskStorage
```
#### Description
The command removes all PersonalvDisk storage from all hosting units called "Host1".
