
# Get-Monitorservicestatus
Gets the current status of the Monitor Service on the controller.
## Syntax

```
Get-MonitorServiceStatus [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Enables the status of the Monitor Service on the controller to be determined. If the service has multiple data stores it will return the overall state as an aggregate of all the data store states. For example, if the site data store status is OK and the secondary data store status is DBUnconfigured then it will return DBUnconfigured. The database connection to the service does not need to be configured before using this command.


## Related Commands

* [Get-MonitorDataStore](../Get-MonitorDataStore/)
* [Set-MonitorDBConnection](../Set-MonitorDBConnection/)
* [Test-MonitorDBConnection](../Test-MonitorDBConnection/)
* [Get-MonitorDBConnection](../Get-MonitorDBConnection/)
* [Get-MonitorDBSchema](../Get-MonitorDBSchema/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a Citrix Virtual Apps and Desktops 7 controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Fma.Sdk.Utilities.Service.Servicestatusinfo
The Get-MonitorServiceStatus command returns an object containing the status of the Monitor Service together with extra diagnostics information.  
OK  
    The Monitor Service is running and is connected to a database containing a valid schema.  
DBUnconfigured  
    The Monitor Service does not have a database connection configured.  
DBRejectedConnection  
    The database rejected the logon attempt from the Monitor Service.  This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.  
InvalidDBConfigured  
    The expected stored procedures are missing from the database.  This may be because the Monitor Service schema has not been added to the database.  
DBNotFound  
    The specified database could not be located with the configured connection string.  
DBMissingOptionalFeature  
    The Monitor is connected to a database that is valid, but it does not have the full functionality required for optimal performance. Upgrading the database is advisable.  
DBMissingMandatoryFeature  
    The Monitor is connected to a database that is valid, but it does not have the full functionality required so the Monitor cannot function. Upgrading the database is required.  
DBNewerVersionThanService  
    The version of the Monitor Service currently in use is incompatible with the version of the Monitor Service schema on the database.  Upgrade the Monitor Service to a more recent version.  
DBOlderVersionThanService  
    The version of the Monitor Service schema on the database is incompatible with the version of the Monitor Service currently in use.  Upgrade the database schema to a more recent version.  
DBVersionChangeInProgress  
    A database schema upgrade is currently in progress.  
PendingFailure  
    Connectivity between the Monitor Service and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
Failed  
    Connectivity between the Monitor and the database has been lost for an extended period of time, or has failed due to a configuration problem. The Monitor service cannot operate while its connection to the database is unavailable.  
Unknown  
    (0) The service status cannot be determined.
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    DatabaseError  
        An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
        The operation could not be completed because the database for the service is not configured.  
    DataStoreException  
        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
    PermissionDenied  
        You do not have permission to execute this command.  
    AuthorizationError  
        There was a problem communicating with the Citrix Delegated Administration Service.  
    CommunicationError  
        There was a problem communicating with the remote service.  
    ExceptionThrown  
        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the Citrix Virtual Apps and Desktops 7 logs.
## Examples

### Example 1

```
C:\PS>Get-MonitorServiceStatus  
  
DBUnconfigured
```

#### Description
Get the current status of the Monitor Service.
