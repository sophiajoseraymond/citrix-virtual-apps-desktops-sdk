﻿
# Unlock-Applibappdisk
Unlocks an AppDisk.
## Syntax

```
Unlock-AppLibAppDisk [-AppDiskName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Unlock-AppLibAppDisk -AppDiskUid <Guid> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to unlockan AppDisk that has the Id of a failed Task still associated with it. This allows another long-running task to operate on that scheme. The cmdlet will not unlock a scheme with a task still marked as being active.  Use Stop-AppLibTask to stop any active task first.


## Related Commands

* [Get-AppLibAppDiske](../Get-AppLibAppDiske/)
* [Stop-AppLibTask](../Stop-AppLibTask/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk. | true | true (ByPropertyName) |  |
| AppDiskUid | The unique identifier of the AppDisk. | true | false |  |
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
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    AppDiskNotFound  
    The specified provisioning scheme could not be located.  
    NoOp  
    The specified provisioning scheme had no task object associated.  
    TaskActive  
    The task object associated with the provisioning scheme is still active.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    CouldNotQuueryDatabase  
    The query required to get the database was not defined.  
    CommunicationError  
    An error occurred while communicating with the service.  
    InvalidFilter  
    A filtering expression was supplied that could not be interpreted for this cmdlet.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Unlock-AppLibAppDisk -AppDiskName MyDisk
```

#### Description
Unlocks the AppDisk 'MyDisk'.
