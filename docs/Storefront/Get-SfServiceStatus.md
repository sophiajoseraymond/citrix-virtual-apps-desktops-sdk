
# Get-Sfservicestatus
Gets the current status of the Storefront Service on the controller.
## Syntax

```
Get-SfServiceStatus [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Enables the status of the Storefront Service on the controller to be determined. The database connection to the service does not need to be configured before using this command.


## Related Commands

* [Set-SfDBConnection](../Set-SfDBConnection/)
* [Test-SfDBConnection](../Test-SfDBConnection/)
* [Get-SfDBConnection](../Get-SfDBConnection/)
* [Get-SfDBSchema](../Get-SfDBSchema/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Fma.Sdk.Utilities.Service.Servicestatusinfo
The Get-SfServiceStatus command returns an object containing the status of the Storefront Service together with extra diagnostics information.  
OK  
    The Storefront Service is running and is connected to a database containing a valid schema.  
DBUnconfigured  
    The Storefront Service does not have a database connection configured.  
DBRejectedConnection  
    The database rejected the logon attempt from the Storefront Service.  This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.  
InvalidDBConfigured  
    The expected stored procedures are missing from the database.  This may be because the Storefront Service schema has not been added to the database.  
DBNotFound  
    The specified database could not be located with the configured connection string.  
DBMissingOptionalFeature  
    The Storefront is connected to a database that is valid, but it does not have the full functionality required for optimal performance. Upgrading the database is advisable.  
DBMissingMandatoryFeature  
    The Storefront is connected to a database that is valid, but it does not have the full functionality required so the Storefront cannot function. Upgrading the database is required.  
DBNewerVersionThanService  
    The version of the Storefront Service currently in use is incompatible with the version of the Storefront Service schema on the database.  Upgrade the Storefront Service to a more recent version.  
DBOlderVersionThanService  
    The version of the Storefront Service schema on the database is incompatible with the version of the Storefront Service currently in use.  Upgrade the database schema to a more recent version.  
DBVersionChangeInProgress  
    A database schema upgrade is currently in progress.  
PendingFailure  
    Connectivity between the Storefront Service and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
Failed  
    Connectivity between the Storefront and the database has been lost for an extended period of time, or has failed due to a configuration problem. The Storefront service cannot operate while its connection to the database is unavailable.  
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
        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Get-SfServiceStatus  
  
DBUnconfigured
```

#### Description
Get the current status of the Storefront Service.
