﻿
# Add-Hypmetadata
Adds metadata to a hypervisor connection or a hosting unit.
## Syntax

```
Add-HypMetadata [-LiteralPath] <String> [-Property] <String> [-Value] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Use this command to store additional custom data against a hosting unit or hypervisor connection.  This data is not used by the Machine Creation Service, and is provided only for consumers of the services to store any data that may be required for their operations.  The metadata is returned along with the hypervisor connection or hosting unit that it is assigned to.


## Related Commands

* [Remove-HypMetadata](../Remove-HypMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a hosting unit provider to the hosting unit or hypervisor connection item to which to add the metadata. The path specified must be in one of the following formats: &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt; or  &lt;drive&gt;:\\HostingUnits\\{&lt;HostingUnit Uid&gt; or  &lt;drive&gt;:\\Connections\\&lt;Connection Name&gt; or  &lt;drive&gt;:\\Connections\\{&lt;Connection Uid&gt;} | true | true (ByValue) |  |
| Property | Specifies the property name of the metadata to be added.  The property must be unique for the item specified by the path.  
The property cannot contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | false |  |
| Value | Specifies the value for the property. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String  
    You Can Pipe A String The Contains A Path To Add-Hypmetadata (Path Parameter).

## Return Values

### Citrix.Host.Sdk.Metadata
Add-HypMetadata returns an object containing the new definition of the metadata.  
    Property &lt;string&gt;  
        Specifies the property of the metadata.  
    Value &lt;string&gt;  
        Specifies the value of the metadata.
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    InvalidPath  
    The path provided is not in the required format.  
    HostingUnitMetadataForeignKeyObjectDoesNotExist  
    The hosting unit supplied in the path does not exist.  
    HypervisorConnectionMetadataForeignKeyObjectDoesNotExist  
    The hypervisor connection supplied in the path does not exist.  
    HostingUnitMetadataDuplicateObjectExists  
    Metadata for the specified hosting unit item already exists with the same property name.  
    HypervisorConnectionMetadataDuplicateObjectExists  
    Metadata for the specified hypervisor connection item already exists with the same property name.  
    MetadataContainerUndefined  
    The specified path does not reference a hosting unit or a hypervisor connection.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    DataStoreException  
    An error occurred in the service while attempting a database operation - communication with the database failed for  
    various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
c:\PS>Add-HypMetadata -LiteralPath XDHyp:\Connections\MyConnection -Property MyProperty -Value MyValue  
  
Property                                                    Value  
  
--------                                                    -----  
  
MyProperty                                                  MyValue
```

#### Description
The command adds the metadata with the property name of "MyProperty" and value of "MyValue" to the hypervisor connection item called "MyConnection".
### Example 2

```
c:\PS>dir xdhyp\connections\Citrix\* | Add-HypMetadata -Property MyProperty -Value MyValue  
  
Property                                                    Value  
  
--------                                                    -----  
  
MyProperty                                                  MyValue  
  
MyProperty                                                  MyValue  
  
MyProperty                                                  MyValue
```

#### Description
The command adds the metadata with the property name of "MyProperty" and value of "MyValue" to all the hypervisor connection items that begin with the string "Citrix".
