
# Rename-Acctidentitypool
Renames an identity pool.
## Syntax

```
Rename-AcctIdentityPool [-IdentityPoolName] <String> [-NewIdentityPoolName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Rename-AcctIdentityPool -IdentityPoolUid <Guid> -NewIdentityPoolName <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to change the name of an existing identity pool.


## Related Commands

* [Get-AcctIdentityPool](../Get-AcctIdentityPool/)
* [Set-AcctIdentityPool](../Set-AcctIdentityPool/)
* [Remove-AcctIdentityPool](../Remove-AcctIdentityPool/)
* [Test-AcctIdentityPoolNameAvailable](../Test-AcctIdentityPoolNameAvailable/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool to be renamed. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool to be renamed. | true | false |  |
| NewIdentityPoolName | The new name for the identity pool.  This must be a name which is not used by an existing identity pool, and it must not contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | true (ByPropertyName) |  |
| PassThru | Defines whether or not the command returns a result showing the new state of the updated provisioning scheme. | false | true (ByPropertyName) | true |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Identitypool
This object provides details of the identity pool and contains the following information:  
IdentityPoolName &lt;string&gt;  
    The name of the identity pool.  
IdentityPoolUid &lt;Guid&gt;  
    The unique identifier for the identity pool.  
NamingScheme &lt;string&gt;  
    The naming scheme for the identity pool.  
NamingSchemeType &lt;Citrix.XDInterServiceTypes.ADIdentityNamingScheme&gt;  
    The naming scheme type for the identity pool. This can be one of the following:  
        Numeric - naming scheme uses numeric indexes  
        Alphabetic - naming scheme uses alphabetic indexes  
StartCount &lt;int&gt;  
    The next index to be used when creating an identity from the identity pool.  
OU &lt;string&gt;  
    The Active Directory distinguished name for the OU in which accounts created from this identity pool will be created.  
Domain &lt;string&gt;  
    The Active Directory domain that accounts in the pool belong to.  
Lock &lt;Boolean&gt;  
    Indicates if the identity pool is locked.
## Notes
In the case of failure the following errors can result.  
    Error Codes  
    -----------  
    IdentityPoolObjectNotFound  
    The specified identity pool could not be located.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with the database failed for  
    for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Rename-AcctIdentityPool -IdentityPoolName oldName -NewIdentityPoolName newName
```

#### Description
Renames an existing identity pool called "oldName" to be called "newName".
