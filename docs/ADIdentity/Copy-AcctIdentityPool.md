
# Copy-Acctidentitypool
Copies an Identity Pool and its associated Identities to a new IdentityPool
## Syntax

```
Copy-AcctIdentityPool [-IdentityPoolName] <String> [-NewIdentityPoolName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Copy-AcctIdentityPool -IdentityPoolUid <Guid> [-NewIdentityPoolName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to copy an IdentityPool.

The new IdentityPool will contain all the accounts that were in the original pool and will have the same domain and OU set. The naming scheme will be unset and the StartCount will be set to 1.


## Related Commands

* [New-AcctIdentityPool](../New-AcctIdentityPool/)
* [Get-AcctIdentityPool](../Get-AcctIdentityPool/)
* [Remove-AcctIdentityPool](../Remove-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool that is to be copied. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool that is to be copied. | true | false |  |
| NewIdentityPoolName | The name for the new IdentityPool. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Identitypool
This object provides details of the new identity pool and contains the following information:  
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
          Indicates whether the identity pool is locked.
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    IdentityPoolDuplicateObjectExists  
    An identity pool with the same name exists already.  
    IdentityPoolObjectNotFound  
    The identity pool to be modified could not be located.  
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

```

#### Description

