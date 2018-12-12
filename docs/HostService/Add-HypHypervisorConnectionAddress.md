
# Add-Hyphypervisorconnectionaddress
Add a connection address to a hypervisor connection.
## Syntax
```
Add-HypHypervisorConnectionAddress [-LiteralPath] <String> [-HypervisorAddress] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to add addresses by which a hypervisor can be contacted.  All addresses added to a single hypervisor connection are assumed to be equivalent (i.e. they all result in the ability to communicate with the same hypervisors).  The hypervisor that the addresses reference is stored at the point of creation of the hypervisor connection. Once this is done, to be valid, all addresses must resolve to this hypervisor.

The addresses required are; XenServer - The address of the XenServer machines (must all reference the same XenServer pool). VMWare vSphere/ESX - The address of a vCenter Server. Microsoft SCVMM/Hyper-V - the address of an SCVMM server.


## Related Commands

* [Remove-HypHypervisorConnectionAddress](./Remove-HypHypervisorConnectionAddress/)
* [Get-HypXenServerAddress](./Get-HypXenServerAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a Host Service provider to the hypervisor connection item to which to add the address. The path specified must be in one of the following formats; &lt;drive&gt;:\\Connections\\&lt;HypervisorConnectionName&gt; or  &lt;drive&gt;:\\Connections\\{HypervisorConnection Uid&gt;} | true | false |  |
| HypervisorAddress | Specifies the address to be used.  The address will be validated and the hypervisor must be contactable at the address supplied.<br>XenServer (ConnectionType = XenServer) The address being added must reference the same XenServer pool referenced by any existing addresses for the same connection. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Host.Sdk.Hypervisorconnection<br>   Add-Hyphypervisorconnectionaddress Returns An Object Containing The New Definition Of The Hypervisor Connection.<br>    Hypervisorconnectionuid &lt;Guid&gt;<br>        Specifies The Unique Identifier For The Hypervisor Connection.<br>    Hypervisorconnectionname &lt;String&gt;<br>        Specifies The Name Of The Hypervisor Connection.<br>    Connectiontype &lt;Citrix.Xdinterservicetypes.Connectiontype&gt;<br>        Specifies The Connection Type Of The Connection.<br>            Xenserver - A Citrix Hypervisor Hypervisor<br>            Scvmm -  A Microsoft Scvmm/Hyper-V Hypervisor<br>            Vcenter -  A Vmware Vsphere/Esx Hypervisor<br>            Custom - A 3Rd Party Hypervisor<br>    Hypervisoraddress &lt;String\[\]&gt;<br>        A List Of Addresses That Can Be Used To Communicate With The Hypervisor.<br>    Username &lt;String&gt;<br>        The User Name That Is Used When Connecting To The Hypervisor.<br>    Persistent &lt;Boolean&gt;<br>        Indicates Whether The Connection Is Stored In The Database Or Is A Temporary Connection Only With The Same Lifetime As The Current Powershell Session.<br>    Pluginid &lt;String&gt;<br>        The Citrix Identifier For The Citrix Machine Management Plug-In.<br>     Revision &lt;Guid&gt;<br>        Identifier For The Current Version Of The Hypervisor Connection.  This Value Changes Every Time A Property Of The Hypervisor Connection Is Updated.<br>    Supportspvsvms &lt;Boolean&gt;<br>        Indicates Whether Or Not The Connection Can Be Used As Part Of A Hosting Unit And Therefore Used By The Citrix Xendesktop Machine Creation Service To Create Virtual Machines.  Only The Built-In Supported Hypervisor Connection Types Can Be Used For This (I.E. Xenserver, Scvmm And Vcenter).<br>    Metadata &lt;Citrix.Host.Sdk.Metadata\[\]&gt;<br>        A List Of Key Value Pairs That Can Store Additional Information Relating To The Hosting Unit.

## Notes
The address format must be valid for the hypervisor connection.  The rules that are applied are as below: XenServer (HypervisorConnection Type = XenServer)<br>    http:\\\\&lt;IP Address&gt;<br>    or http:\\\\&lt;server Name&gt;<br>    or https:\\\\&lt;server Name&gt;<br>    Note:  To use multiple addresses to the same XenServer pool to provide failover functionality, all XenServers in the pool must have a shared block storage device.  If the use of https connections and failover is required, the certificates on the servers must be trusted by all of the controllers (typically this means having a root certificate installed).<br>    Note: If XenServers are moved to new XenServer pools after being added to a hypervisor connection, unpredictable results can occur.  Once a XenServer is assigned to a hypervisor connection, it must not be moved to a new XenServer pool.<br>    In the case of failure the following errors can result.<br>    Error Codes<br>    -----------<br>    InputConnectionsPathInvalid<br>    The path provided is not to an item in a sub directory of a hosting unit item.<br>    HypervisorConnectionAddressForeignKeyObjectDoesNotExist<br>    The hypervisor connection to which the address is to be added could not be located.<br>    ConnectionAddressInvalid<br>    The address could not be used to contact a hypervisor or the validation rules have not been met.<br>    HypervisorConnectionAddressDuplicateObjectExists<br>    The address specified is already part of the hypervisor connection.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
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
