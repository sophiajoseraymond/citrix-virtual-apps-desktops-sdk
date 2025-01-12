﻿
# Remove-Acctidentitypool
Removes identity pools.
## Syntax

```
Remove-AcctIdentityPool [-IdentityPoolName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Remove-AcctIdentityPool -IdentityPoolUid <Guid> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to remove identity pools.  The identity pool must be emptied of any AD accounts that it contains before it can be removed.


## Related Commands

* [New-AcctIdentityPool](../New-AcctIdentityPool/)
* [Rename-AcctIdentityPool](../Rename-AcctIdentityPool/)
* [Set-AcctIdentityPool](../Set-AcctIdentityPool/)
* [Unlock-AcctIdentityPool](../Unlock-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool to remove. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool to remove. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Notes
In the case of failure the following errors can be produced.  
    Error Codes  
    -----------  
    IdentityPoolObjectNotFound  
    The specified identity pool could not be located.  
    UnableToRemoveDueToAssociatedAccounts  
    The identity pool is not empty.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with the database failed for  
    for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1

```
c:\Remove-AcctIdentityPool -IdentityPoolName MyPool
```

#### Description
Removes the identity pool called "MyPool".
