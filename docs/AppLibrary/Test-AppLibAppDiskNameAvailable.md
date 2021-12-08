
# Test-Applibappdisknameavailable
Checks to ensure that the proposed name for an AppDisk is unused.
## Syntax

```
Test-AppLibAppDiskNameAvailable -AppDiskName <String[]> [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Checks to ensure that the proposed name for an AppDisk is unused. This check is done without regard for scoping of existing AppDisks, so the names of inaccessible AppDisks are also checked.


## Related Commands

* [New-AppLibAppDisk](../New-AppLibAppDisk/)
* [Rename-AppLibAppDisk](../Rename-AppLibAppDisk/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name or names of the provisioning scheme(s) to be tested. | true | true (ByValue, ByPropertyName) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Nameavailability
Pairs of name and the availability of the name
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with the database failed for  
    for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
Test-AppLibAppDiskNameAvailable -AppDiskName $NewDiskName
```

#### Description
This tests whether the value of \$NewDiskName is unique or not, and can be used to create a new AppDisk or rename an existing one without failing. True is returned if the name is good.
