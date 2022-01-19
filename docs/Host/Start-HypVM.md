
# Start-Hypvm
Starts a VM.
## Syntax

```
Start-HypVM [-LiteralPath] <String> [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
This command provides a mechanism to start a VM.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a hosting unit provider to the virtual machine item to start. The path specified must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;Connection Name&gt;\\&lt;Item Path of VM object&gt; or  &lt;drive&gt;:\\Connections\\{&lt;connection Uid&gt;\\&lt;Item Path of VM object&gt;} or &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnit Name&gt;\\&lt;Item Path of VM object&gt; or  &lt;drive&gt;:\\HostingUnits\\{&lt;hostingUnit Uid&gt;\\&lt;Item Path of VM object&gt;} | true | true (ByValue) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String  
          You Can Pipe A String That Contains A Path.

## Return Values

### System.Void.

## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    InputHypervisorItemPathInvalid  
    The path provided is not to an item in a sub-directory of a connection item or a hosting unit item.  
    InvalidHypervisorItemPath  
    No item exists with the specified path.  
    InvalidHypervisorItem  
    The item specified by the path exists, but is not a VM Item.  
    HypervisorInMaintenanceMode  
    The hypervisor is in maintenance mode.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    CommunicationError  
    An error occurred while communicating with the service.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ExceptionThrown  
    An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Start-HypVM -LiteralPath XDHyp:\Connections\MyConnection\MyVm.vm
```

#### Description
This command starts a VM called 'MyVm.vm' within a hypervisor connection called 'MyConnection'.
