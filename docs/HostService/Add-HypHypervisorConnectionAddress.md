
# Add-Hyphypervisorconnectionaddress
Add a connection address to a hypervisor connection.
## Syntax

```
Add-HypHypervisorConnectionAddress [-LiteralPath] <String> [-HypervisorAddress] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Use this command to add addresses by which a hypervisor can be contacted.  All addresses added to a single hypervisor connection are assumed to be equivalent (i.e. they all result in the ability to communicate with the same hypervisors).  The hypervisor that the addresses reference is stored at the point of creation of the hypervisor connection. Once this is done, to be valid, all addresses must resolve to this hypervisor.

The addresses required are; XenServer - The address of the XenServer machines (must all reference the same XenServer pool). VMWare vSphere/ESX - The address of a vCenter Server. Microsoft SCVMM/Hyper-V - the address of an SCVMM server.


## Related Commands

* [Remove-HypHypervisorConnectionAddress](../Remove-HypHypervisorConnectionAddress/)
* [Get-HypXenServerAddress](../Get-HypXenServerAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a Host Service provider to the hypervisor connection item to which to add the address. The path specified must be in one of the following formats; &lt;drive&gt;:\\Connections\\&lt;HypervisorConnectionName&gt; or  &lt;drive&gt;:\\Connections\\{HypervisorConnection Uid&gt;} | true | false |  |
| HypervisorAddress | Specifies the address to be used.  The address will be validated and the hypervisor must be contactable at the address supplied.  
XenServer (ConnectionType = XenServer) The address being added must reference the same XenServer pool referenced by any existing addresses for the same connection. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Host.Sdk.Hypervisorconnection
Add-HypHypervisorConnectionAddress returns an object containing the new definition of the hypervisor connection.  
    HypervisorConnectionUid &lt;Guid&gt;  
        Specifies the unique identifier for the hypervisor connection.  
    HypervisorConnectionName &lt;string&gt;  
        Specifies the name of the hypervisor connection.  
    ConnectionType &lt;Citrix.XDInterServiceTypes.ConnectionType&gt;  
        Specifies the connection type of the connection.  
            XenServer - A Citrix Hypervisor hypervisor  
            SCVMM -  A Microsoft SCVMM/Hyper-V hypervisor  
            vCenter -  A VMWare vSphere/ESX hypervisor  
            Custom - A 3rd party hypervisor  
    HypervisorAddress &lt;string\[\]&gt;  
        A list of addresses that can be used to communicate with the hypervisor.  
    UserName &lt;string&gt;  
        The user name that is used when connecting to the hypervisor.  
    Persistent &lt;Boolean&gt;  
        Indicates whether the connection is stored in the database or is a temporary connection only with the same lifetime as the current Powershell session.  
    PlugInId &lt;string&gt;  
        The Citrix identifier for the Citrix Machine Management plug-in.  
     Revision &lt;Guid&gt;  
        Identifier for the current version of the hypervisor connection.  This value changes every time a property of the hypervisor connection is updated.  
    SupportsPvsVMs &lt;Boolean&gt;  
        Indicates whether or not the connection can be used as part of a hosting unit and therefore used by the Citrix XenDesktop Machine Creation Service to create virtual machines.  Only the built-in supported hypervisor connection types can be used for this (i.e. XenServer, SCVMM and vCenter).  
    Metadata &lt;Citrix.Host.Sdk.Metadata\[\]&gt;  
        A list of key value pairs that can store additional information relating to the hosting unit.
## Notes
The address format must be valid for the hypervisor connection.  The rules that are applied are as below: XenServer (HypervisorConnection Type = XenServer)  
    http:\\\\&lt;IP Address&gt;  
    or http:\\\\&lt;server Name&gt;  
    or https:\\\\&lt;server Name&gt;  
    Note:  To use multiple addresses to the same XenServer pool to provide failover functionality, all XenServers in the pool must have a shared block storage device.  If the use of https connections and failover is required, the certificates on the servers must be trusted by all of the controllers (typically this means having a root certificate installed).  
    Note: If XenServers are moved to new XenServer pools after being added to a hypervisor connection, unpredictable results can occur.  Once a XenServer is assigned to a hypervisor connection, it must not be moved to a new XenServer pool.  
    In the case of failure the following errors can result.  
    Error Codes  
    -----------  
    InputConnectionsPathInvalid  
    The path provided is not to an item in a sub directory of a hosting unit item.  
    HypervisorConnectionAddressForeignKeyObjectDoesNotExist  
    The hypervisor connection to which the address is to be added could not be located.  
    ConnectionAddressInvalid  
    The address could not be used to contact a hypervisor or the validation rules have not been met.  
    HypervisorConnectionAddressDuplicateObjectExists  
    The address specified is already part of the hypervisor connection.  
    HypervisorInMaintenanceMode  
    The hypervisor for the connection is in maintenance mode.  
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
c:\PS>Add-HypHypervisorConnectionAddress -LiteralPath XDHyp:\Connections\MyConnection -HypervisorAddress http:\\myserver.com  
  
PSPath                   : Citrix.HostingUnitService.Admin.V1.0\Citrix.Hypervisor::XDHyp:\Connections\MyConnection  
  
PSParentPath             : Citrix.HostingUnitService.Admin.V1.0\Citrix.Hypervisor::XDHyp:\Connections  
  
PSChildName              : MyConnection  
  
PSDrive                  : XDHyp  
  
PSProvider               : Citrix.HostingUnitService.Admin.V1.0\Citrix.Hypervisor  
  
PSIsContainer            : True  
  
HypervisorConnectionUid  : 85581f42-c5da-4976-970c-ebc3448ea1e3  
  
HypervisorConnectionName : MyConnection  
  
ConnectionType           : XenServer  
  
HypervisorAddress        : {http:\\myserver2.com,http:\\myserver.com}  
  
UserName                 : root  
  
Persistent               : False  
  
PluginId                 : XenFactory  
  
SupportsPvsVMs           : True  
  
Revision                 : 4c95c857-c54d-4f92-abef-0cce32c02502  
  
Metadata                 :
```

#### Description
Add the address 'http:\\\\myserver.com' to the hypervisor connection called "MyConnection".
