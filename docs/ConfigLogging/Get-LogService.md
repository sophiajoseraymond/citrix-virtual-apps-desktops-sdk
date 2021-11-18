
# Get-Logservice
Gets the service record entries for the ConfigurationLogging Service.
## Syntax

```
Get-LogService [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Returns instances of the ConfigurationLogging Service that the service publishes.  The service records contain account security identifier information that can be used to remove each service from the database.

A database connection for the service is required to use this command.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Metadata | Gets records with matching metadata entries.  
The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Log\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_Log\_Filtering for details. | false | false |  |
| FilterScope | Gets only results allowed by the specified scope id. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Configurationlogging.Sdk.Service
The Get-LogServiceInstance command returns an object containing the following properties.  
Uid &lt;Integer&gt;  
    Specifies the unique identifier for the service in the group.  The unique identifier is an index number.  
ServiceHostId &lt;Guid&gt;  
    Specifies the unique identifier for the service instance.  
DNSName &lt;String&gt;  
    Specifies the domain name of the host on which the service runs.  
MachineName &lt;String&gt;  
    Specifies the short name of the host on which the service runs.  
CurrentState &lt;Citrix.Fma.Sdk.ServiceCore.ServiceState&gt;  
    Specifies whether the service is running, started but inactive, stopped, or failed.  
LastStartTime &lt;DateTime&gt;  
    Specifies the date and time at which the service was last restarted.  
LastActivityTime &lt;DateTime&gt;  
    Specifies the date and time at which the service was last stopped or restarted.  
OSType  
    Specifies the operating system installed on the host on which the service runs.  
OSVersion  
    Specifies the version of the operating system installed on the host on which the service runs.  
ServiceVersion  
    Specifies the version number of the service instance.  The version number is a string that reflects the full build version of the service.  
DatabaseUserName &lt;string&gt;  
    Specifies for the service instance the Active Directory account name with permissions to access the database.  This will be either the machine account or, if the database is running on a controller, the NetworkService account.  
Sid &lt;string&gt;  
    Specifies the Active Directory account security identifier for the machine on which the service instance is running.  
ActiveSiteServices &lt;string\[\]&gt;  
    Specifies the names of active site services currently running in the service. Site services are components that perform long-running background processing in some services. This field is empty for services that do not contain site services.
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    UnknownObject  
        One of the specified objects was not found.  
    PartialData  
         Only a subset of the available data was returned.  
    InvalidFilter  
        A filtering expression was supplied that could not be interpreted for this cmdlet.  
    CouldNotQueryDatabase  
         The query required to get the database was not defined.  
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
c:\PS>Get-LogService  
  
Uid                : 1  
  
ServiceHostId      : aef6f464-f1ee-4042-a523-66982e0cecd0  
  
DNSName            : MyServer.company.com  
  
MachineName        : MYSERVER  
  
CurrentState       : On  
  
LastStartTime      : 04/04/2011 15:25:38  
  
LastActivityTime   : 04/04/2011 15:33:39  
  
OSType             : Win32NT  
  
OSVersion          : 6.1.7600.0  
  
ServiceVersion     : 5.1.0.0  
  
DatabaseUserName   : NT AUTHORITY\NETWORK SERVICE  
  
SID                : S-1-5-21-2316621082-1546847349-2782505528-1165  
  
ActiveSiteServices : {MySiteService1, MySiteService2...}
```

#### Description
Get all the instances of the ConfigurationLogging Service running in the current service group.
