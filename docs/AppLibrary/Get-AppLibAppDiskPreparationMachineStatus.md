
# Get-Applibappdiskpreparationmachinestatus
Gets the status of a preparation machine being used by an AppDisk.
## Syntax

```
Get-AppLibAppDiskPreparationMachineStatus -AppDiskUid <Guid> [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Get-AppLibAppDiskPreparationMachineStatus [-AppDiskName] <String> [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Machines within a Machine Catalog are reserved temporarily during a number of AppDisk operations, including creation and import. This cmdlet returns the machine name, power state and registration state of the machine currently assigned as the preparation machine for the given AppDisk. If the AppDisk has no associated preparation machine, no result will be returned.


## Related Commands

* [Get-AppLibAppDisk](../Get-AppLibAppDisk/)
* [New-AppLibAppDisk](../New-AppLibAppDisk/)
* [Import-AppLibAppDisk](../Import-AppLibAppDisk/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk. | true | false |  |
| AppDiskUid | The unique identifier of the AppDisk. | true | true (ByPropertyName) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appdiskpreparationmachinestatus
This object provides details of the AppDisk preparation machine and contains the following information:  
          AppDiskUid &lt;Guid&gt;  
          The unique identifier for the AppDisk.  
          AppDiskName &lt;string&gt;  
          The name of the AppDisk.  
          MachineName &lt;string&gt;  
          The name of the preparation machine.  
          PowerState &lt;Citrix.AppLibrary.Sdk.BrokerPowerState&gt;  
          The current power state of the machine. Possible values are: Unmanaged, Unknown, Unavailable, Off,  
          On, Suspended, TurningOn, TurningOff, Suspending, Resuming.  
          RegistrationState &lt;Citrix.AppLibrary.Sdk.BrokerRegistrationState&gt;  
          Indicates the registration state of the machine. Possible values are: Unregistered, Initializing,  
          Registered, AgentError.
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with the database failed  
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
PS C:\> Get-AppLibAppDiskPreparationMachineStatus -AppDiskName Disk1  
  
AppDiskName       : Disk1  
  
AppDiskUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42  
  
MachineName       : WWCO\Machine01  
  
PowerState        : On  
  
RegistrationState : Registered
```

#### Description
Gets the status of the preparation machine currently associated with the given AppDisk.
