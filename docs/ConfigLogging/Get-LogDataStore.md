
# Get-Logdatastore
Gets details for each of the ConfigurationLogging data stores.
## Syntax

```
Get-LogDataStore [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Returns an object for each of the ConfigurationLogging data stores describing the connection string, data store name, db type, provider, schema name, and DB status.

A database connection must be configured in order for this command to be used if the service has a secondary data store. This is not required for the site data store.


## Related Commands

* [Reset-LogDataStore](../Reset-LogDataStore/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Configurationlogging.Sdk.Datastoreconfiguration
An object describing the connection string, data store name, database type, provider, schema name and database status.
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
c:\PS>Get-LogDataStore  
  
ConnectionString : Server=.\SQLEXPRESS;Initial Catalog = databaseName; Integrated Security = True  
  
DataStore        : Site  
  
DatabaseType     : SqlServer  
  
Provider         : MSSQL  
  
SchemaName       : LogSiteSchema  
  
Status           : OK  
  
ConnectionString :  
  
DataStore        : Secondary  
  
DatabaseType     : SqlServer  
  
Provider         : MSSQL  
  
SchemaName       : LogSecondarySchema  
  
Status           : DBUnconfigured
```

#### Description
Get the database connection string for the ConfigurationLogging Service.
