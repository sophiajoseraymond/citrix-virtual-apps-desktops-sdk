
# Remove-Hyphostingunitstorage
Removes storage from a hosting unit.
## Syntax

```
Remove-HypHostingUnitStorage [-LiteralPath] <String> [-StoragePath <String>] [-StorageType <StorageType>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
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
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. This can be a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String  
    You Can Pipe A String That Contains A Path To Remove-Hyphostingunitstorage (Storagepath Parameter).

## Return Values

### Citrix.Xdpowershell.Hostingunit
Remove-HypHostingUnitStorage returns an object containing the new definition of the hosting unit.  
    HostingUnitUid &lt;Guid&gt;  
        Specifies the unique identifier for the hosting unit.  
    HostingUnitName &lt;string&gt;  
        Specifies the name of the hosting unit.  
    HypervisorConnection &lt;Citrix.XDPowerShell.HypervisorConnection&gt;  
        Specifies the connection that the hosting unit uses to access a hypervisor.  
    RootId &lt;string&gt;  
        Identifies, to the hypervisor, the root of the hosting unit.  
    RootPath &lt;string&gt;  
        The hosting unit provider path that represents the root of the hosting unit.  
    Storage &lt;Citrix.XDPowerShell.Storage\[\]&gt;  
        The list of storage items that the hosting unit can use.  
    PersonalvDiskStorage &lt;Citrix.XDPowerShell.Storage\[\]&gt;  
        The list of storage items that the hosting unit can use for storing personal data.  
    VMTaggingEnabled &lt;Boolean&gt;  
        Specifies whether or not the metadata in the hypervisor can be used to store information about the XenDesktop Machine Creation Service.  
    NetworkId &lt;string&gt;  
        The hypervisor's internal identifier that represents the network specified for the hosting unit.  
    NetworkPath &lt;string&gt;  
        The hosting unit provider path to the network specified for the hosting unit.  
    AdditionalStorage  
        The list of additional storage items that the hosting unit can use.  
    Metadata &lt;Citrix.XDPowerShell.Metadata\[\]&gt;  
        A list of key value pairs that can store additional information about the hosting unit.
## Notes
After storage is removed, it is the administrator's responsibility to maintain its contents. The Citrix XenDesktop Machine Creation Service does not attempt to clean up any data that is stored in the storage location.  
    If all storage is removed from the hosting unit, other features of the Machine Creation Service stops functioning until some storage is added again.  
    In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    HostingUnitsPathInvalid  
    The path provided is not to an item in a subdirectory of a hosting unit item.  
    HostingUnitStorageObjectToDeleteDoesNotExist  
    The storage path specified is not part of the hosting unit.  
    HypervisorInMaintenanceMode  
    The hypervisor for the connection is in maintenance mode.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    DataStoreException  
    An error occurred in the service while attempting a database operation. Communication with the database failed for  
    for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ExceptionThrown  
    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
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
