
# Set-Configdbconnection
Configures a database connection for the Configuration Service.
## Syntax

```
Set-ConfigDBConnection [-DBConnection] <String> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Specifies the database connection string for use by the currently selected Citrix Configuration Service instance.

The service records the connection string and attempts to contact the specified database. If the database cannot initially be contacted the service retries the connection at intervals until contact with the database is successfully established.

Is is not possible to set a new database connection string for the service if one is already recorded. The connection string must first be set to \$null. This action causes the service to reset and return to its idle state, at which point a new connection string can be set.

When a database connection string is successfully set for the service, a status of OK is returned by the cmdlet. If the database connection string is set to \$null, a DBUnconfigured status is returned.

A syntactically invalid connection string is not recorded.

Only use of Windows authentication within the connection string is supported; a connection string containing SQL authentication credentials is always rejected as invalid.

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a Configuration SDK cmdlet.


## Related Commands

* [Get-ConfigServiceStatus](../Get-ConfigServiceStatus/)
* [Get-ConfigDBConnection](../Get-ConfigDBConnection/)
* [Test-ConfigDBConnection](../Test-ConfigDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DBConnection | Specifies the database connection string to be used by the Configuration Service.  Passing in \$null will clear any existing database connection configured. | true | false |  |
| Force | If present, allows the local administrator to set the connection string to null when there are problems contacting the database or other services. | false | false | false |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
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
The Set-ConfigDBConnection cmdlet returns an object describing the status of the Configuration Service together with extra diagnostics information. Possible values are:  
-- OK:  
The Configuration Service instance is configured with a valid database and service schema. The service is operational.  
-- DBUnconfigured:  
No database connection string is set for the Configuration Service instance.  
-- DBRejectedConnection:  
The database rejected the logon attempt from the Configuration Service. This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.  
-- InvalidDBConfigured:  
The specified database does not exist, is not visible to the Configuration Service instance, or the service's schema within the database is invalid.  
-- DBNotFound:  
The specified database could not be located with the configured connection string.  
-- DBNewerVersionThanService:  
The version of the Configuration Service currently in use is newer than, and incompatible with, the version of the Configuration Service schema on the database. Upgrade the Configuration Service to a more recent version.  
-- DBOlderVersionThanService:  
The version of the Configuration Service schema on the database is newer than, and incompatible with, the version of the Configuration Service currently in use. Upgrade the database schema to a more recent version.  
-- DBVersionChangeInProgress:  
A database schema upgrade is in progress.  
-- PendingFailure:  
Connectivity between the Configuration Service instance and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
-- Failed:  
Connectivity between the Configuration Service instance and the database has been lost for an extended period of time, or has failed due to a configuration problem. The service instance cannot operate while its connection to the database is unavailable.  
-- Unknown:  
The status of the Configuration Service cannot be determined.
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    InvalidDBConnectionString  
        The database connection string has an invalid format.  
    DatabaseConnectionDetailsAlreadyConfigured  
        There was already a database connection configured. After a configuration is set, it can only be set to \$null.  
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
C:\PS>Set-ConfigDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
```

#### Description
Configures the service instance to use a database called XDDB on an SQL Server Express database running on the machine called dbserver. Integrated Windows authentication is required.
### Example 2

```
C:\PS>Set-ConfigDBConnection -DBConnection $null
```

#### Description
Resets the service instance's database connection string. The service instance resets and returns to an idle state until a valid new database connection string is specified.
### Example 3

```
c:\PS>Set-ConfigDBConnection -DBConnection "Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True"  
  
          OK
```

#### Description
Configures a database connection string for the Configuration Service.
### Example 4

```
c:\PS>Set-ConfigDBConnection -DBConnection "Invalid Connection String"  
  
          Invalid database connection string format.
```

#### Description
Configures an invalid database connection string for the Configuration Service.
