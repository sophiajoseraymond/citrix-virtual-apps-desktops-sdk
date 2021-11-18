
# Test-Logdbconnection
Tests whether a database is suitable for use by the Citrix ConfigurationLogging Service.
## Syntax

```
Test-LogDBConnection [-DBConnection] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [[-DataStore] <String>] [<CommonParameters>]
```

## Detailed Description
Tests whether the database specified in the given connection string is suitable for use by the currently selected Citrix ConfigurationLogging Service instance.

The service attempts to contact the specified database and returns a status indicating whether the database is both contactable and usable. The test does not impact any currently established connection from the service instance to another database in any way. The tested connection string is not recorded.

Only use of Windows authentication within the connection string is supported; a connection string containing SQL authentication credentials is always rejected as invalid.

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a ConfigurationLogging SDK cmdlet.


## Related Commands

* [Get-LogServiceStatus](../Get-LogServiceStatus/)
* [Get-LogDBConnection](../Get-LogDBConnection/)
* [Set-LogDBConnection](../Set-LogDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DBConnection | Specifies the database connection string to be tested by the currently selected Citrix ConfigurationLogging Service instance. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |
| DataStore | Specifies the logical name of the data store for the ConfigurationLogging Service. Can be either 'Site' or the logical name of the secondary data store. | false | false | Site |

## Input Type

### 

## Return Values

### Citrix.Fma.Sdk.Utilities.Service.Servicestatusinfo
The Test-LogDBConnection cmdlet returns an object of type ServiceStatusInfo describing the changes to the system that would result from using the specified connection string with the Set-LogDBConnection cmdlet. The actual state of the system is not changed.  
The returned ServiceStatusInfo object has two properties: ServiceStatus, which gives the status of the selected ConfigurationLogging Service instance that would result from adopting the connection string, and ExtraInfo, which is a dictionary providing extra diagnostics information for the database identified by the connection string.  
Possible ServiceStatus values are:  
-- OK:  
The Set-LogDBConnection command would succeed if it were executed with the supplied connection string.  
-- DBUnconfigured:  
No database connection string is set for the service instance.  
-- DBRejectedConnection:  
The database rejected the logon attempt from the ConfigurationLogging Service instance. This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.  
-- InvalidDBConfigured:  
The specified database does not exist, is not visible to the ConfigurationLogging Service instance, or the service's schema within the database is invalid.  
-- DBNotFound:  
The specified database could not be located with the given connection string.  
-- DBNewerVersionThanService:  
The ConfigurationLogging Service instance is older than, and incompatible with, the service's schema in the database. The service instance needs upgrading.  
-- DBOlderVersionThanService:  
The ConfigurationLogging Service instance is newer than, and incompatible with, the service's schema in the database. The database schema needs upgrading.  
-- DBVersionChangeInProgress:  
A database schema upgrade is currently in progress.  
-- PendingFailure:  
Connectivity between the ConfigurationLogging Service instance and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
-- Failed:  
Connectivity between the ConfigurationLogging Service instance and the database has been lost for an extended period of time, or has failed due to a configuration problem. The service instance cannot operate while its connection to the database is unavailable.  
-- Unknown:  
Service status cannot be determined.  
The ExtraInfo dictionary contains at least the following keys, and their associated string values:  
-- Server.Version:  
Database server version number.  
-- Server.IsClustered:  
"True" if the database server is clustered; "False" otherwise.  
-- Database.Status:  
Status of the database. When operating normally, the value is "Normal".  
-- Database.RecoveryModel:  
Recovery model of the database (e.g. "Simple").  
-- Database.LastBackupDate:  
Date of the last backup of this database.  
-- Database.IsReadCommittedSnapshotOn:  
"True" if the READ\_COMMITTED\_SNAPSHOT database option is enabled; "False" otherwise.  
-- Database.Collation:  
Collation order of the database (e.g. "Latin1\_General\_100\_CI\_AS\_KS").  
-- Database.IsMirroringEnabled:  
"True" if the database is mirrored; "False" otherwise.  
-- Database.AvailabilityGroupName:  
The name of the availability group of which this database is a member.  
Beware that the corresponding values are always strings. Therefore, to test Boolean values, you must use statements like  
if (\$info\["Server.IsClustered"\] == "True")  
instead of just  
if (\$info\["Server.IsClustered"\])
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    InvalidDBConnectionString  
        The database connection string has an invalid format.  
    DatabaseError  
        An error occurred in the service while attempting a database operation.  
    DataStoreException  
        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
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
C:\PS>Test-LogDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
```

#### Description
Tests whether the service instance could use a database called XDDB on an SQL Server Express database running on the machine called dbserver. Integrated Windows authentication is required.
### Example 2

```
c:\PS>Test-LogDBConnection -DBConnection "Invalid Connection String"  
  
          Invalid database connection string format.
```

#### Description
Tests an invalid database connection string for the ConfigurationLogging Service.
