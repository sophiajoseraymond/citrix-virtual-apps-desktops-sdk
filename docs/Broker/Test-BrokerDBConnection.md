
# Test-Brokerdbconnection
Tests whether a database is suitable for use by the Citrix Broker Service.
## Syntax

```
Test-BrokerDBConnection [-DBConnection] <String> [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
Tests whether the database specified in the given connection string is suitable for use by the currently selected Citrix Broker Service instance.

The service attempts to contact the specified database and returns a status indicating whether the database is both contactable and usable. The test does not impact any currently established connection from the service instance to another database in any way. The tested connection string is not recorded.

Only use of Windows authentication within the connection string is supported; a connection string containing SQL authentication credentials is always rejected as invalid.

The current service instance is the one on the local machine, or the one most recently specified using the -AdminAddress parameter of a Broker SDK cmdlet.


## Related Commands

* [Get-BrokerServiceStatus](../Get-BrokerServiceStatus/)
* [Get-BrokerDBConnection](../Get-BrokerDBConnection/)
* [Set-BrokerDBConnection](../Set-BrokerDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DBConnection | Specifies the database connection string to be tested by the currently selected Citrix Broker Service instance. | true | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Fma.Sdk.Utilities.Service.Servicestatusinfo
The Test-BrokerDBConnection cmdlet returns an object describing the status of the selected Broker Service instance that would result if the connection string were used with the Set-BrokerDBConnection cmdlet together with extra diagnostics information for the specified connection string. The actual current status of the service is not changed. Possible diagnostic values are:  
-- OK:  
The Set-BrokerDBConnection command would succeed if it were executed with the supplied connection string.  
-- DBUnconfigured:  
No database connection string is set for the service instance.  
-- DBRejectedConnection:  
The database rejected the logon attempt from the Broker Service instance. This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.  
-- InvalidDBConfigured:  
The specified database does not exist, is not visible to the Broker Service instance, or the service's schema within the database is invalid.  
-- DBNotFound:  
The specified database could not be located with the given connection string.  
-- DBNewerVersionThanService:  
The Broker Service instance is older than, and incompatible with, the service's schema in the database. The service instance needs upgrading.  
-- DBOlderVersionThanService:  
The Broker Service instance is newer than, and incompatible with, the service's schema in the database. The database schema needs upgrading.  
-- DBVersionChangeInProgress:  
A database schema upgrade is currently in progress.  
-- PendingFailure:  
Connectivity between the Broker Service instance and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
-- Failed:  
Connectivity between the Broker Service instance and the database has been lost for an extended period of time, or has failed due to a configuration problem. The service instance cannot operate while its connection to the database is unavailable.  
-- Unknown:  
Service status cannot be determined.
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    InvalidDBConnectionString  
        The database connection string has an invalid format.  
    PermissionDenied  
        You do not have permission to execute this command.  
    AuthorizationError  
        There was a problem communicating with the Citrix Delegated Administration Service.  
    ConfigurationLoggingError  
        The operation could not be performed because of a configuration logging error.  
    CommunicationError  
        There was a problem communicating with the remote service.  
    ExceptionThrown  
        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Test-BrokerDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
```

#### Description
Tests whether the service instance could use a database called XDDB on an SQL Server Express database running on the machine called dbserver. Integrated Windows authentication is required.
