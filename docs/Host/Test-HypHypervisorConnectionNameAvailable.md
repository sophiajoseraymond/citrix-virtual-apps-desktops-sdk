
# Test-Hyphypervisorconnectionnameavailable
Checks to ensure that the proposed name for a hypervisor connection is unused.
## Syntax

```
Test-HypHypervisorConnectionNameAvailable -HypervisorConnectionName <String[]> [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Use this command to check that the proposed name for a hypervisor connection is unused. This check is done without regard for scoping of the existing hypervisor connection, so the names of inaccessible hypervisor connection are also checked.


## Related Commands

* [New-Item](../New-Item/)
* [Rename-Item](../Rename-Item/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| HypervisorConnectionName | The name or names of the hypervisor connection(s) to be tested. | true | true (ByValue, ByPropertyName) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Object\[\]
An array of PSObjects which pair the name and availability of the name
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
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
Test-HypHypervisorConnectionNameAvailable -HypervisorConnectionName $NewConnectionName
```

#### Description
This tests whether the value of \$NewConnectionName is unique or not, and can be used to create a new hypervisor connection or rename an existing one. True is returned if the name is unique.
