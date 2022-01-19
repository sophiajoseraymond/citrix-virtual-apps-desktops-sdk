
# Get-Logdbconnection
Gets the database string for the specified data store used by the ConfigurationLogging Service.
## Syntax

```
Get-LogDBConnection [[-DataStore] <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Returns the database connection string from the currently selected ConfigurationLogging Service instance.

If the returned string is blank, no valid connection string has been specified. In this case the service is running, but is idle and awaiting specification of a valid connection string.

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a ConfigurationLogging SDK cmdlet.


## Related Commands

* [Get-LogServiceStatus](../Get-LogServiceStatus/)
* [Get-LogDataStore](../Get-LogDataStore/)
* [Set-LogDBConnection](../Set-LogDBConnection/)
* [Test-LogDBConnection](../Test-LogDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DataStore | Specifies the logical name of the data store for the ConfigurationLogging Service. Can be either be 'Site' or the logical name of the secondary data store. | false | false | Site |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
The database connection string configured for the current ConfigurationLogging Service instance.
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    NoDBConnections  
        The database connection string for the ConfigurationLogging Service has not been specified.  
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
c:\PS>Get-LogDBConnection  
  
Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True
```

#### Description
Get the database connection string for the ConfigurationLogging Service.
