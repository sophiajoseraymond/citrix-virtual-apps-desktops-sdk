
# Set-Acctidentitypool
Update parameters of an identity pool.
## Syntax

```
Set-AcctIdentityPool [-IdentityPoolName] <String> [-NamingScheme <String>] [-NamingSchemeType <ADIdentityNamingScheme>] [-OU <String>] [-Domain <String>] [-AllowUnicode] [-PassThru] [-StartCount <Int32>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-AcctIdentityPool -IdentityPoolUid <Guid> [-NamingScheme <String>] [-NamingSchemeType <ADIdentityNamingScheme>] [-OU <String>] [-Domain <String>] [-AllowUnicode] [-PassThru] [-StartCount <Int32>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to modify the parameters of an identity pool.

Note: When changing a naming scheme or naming scheme type, the index is not reset to 0; it continues to avoid AD account name clashes with existing accounts.  If required, use the New-AcctAdAccount command to change the index when creating further accounts.


## Related Commands

* [New-AcctIdentityPool](../New-AcctIdentityPool/)
* [Get-AcctIdentityPool](../Get-AcctIdentityPool/)
* [Remove-AcctIdentityPool](../Remove-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool that is to be modified. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool that is to be updated. | true | false |  |
| NamingScheme | The new naming scheme that is to be used for the identity pool. | false | false |  |
| NamingSchemeType | The new naming scheme type that is to be used for the identity pool.  This can be Numeric or Alphabetic. | false | false |  |
| OU | The new OU to be used for the Identity Pool.  All accounts created after this is set are created in this AD container.  This will not move any of the existing accounts.  The OU must be a valid AD container and of the domain specified for the pool. | false | false |  |
| Domain | The new Active Directory domain that is to be used for the identity pool.  All new accounts will be created in this domain, but this will not impact any of the existing accounts.  The domain can be specified in either long or short form (i.e. domain or domain.com). | false | false |  |
| AllowUnicode | Updates the definition of the allowed characters in a naming scheme. | false | false |  |
| PassThru | Defines whether the command returns the new state of the identity pool or not. | false | false | false |
| StartCount | The start index for the next create operation | false | false |  |
| ZoneUid | The UID that corresponds to the Zone in which these AD accounts will be created. This is only intended to be used for Citrix Cloud Delivery Controllers. | false | false |  |
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
    Indicates whether the identity pool is locked.
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    InvalidIdentityPoolParameterCombination  
    Caused by either of the following validation errors:  
    \* If an OU is specified then a domain must also be specified.  
    \* NamingScheme, NamingSchemeType and Domain must all be present if any of them are specified.  
    NamingSchemeIllegalComputerName  
    The naming scheme supplied is not valid.  
    UnableToConvertDomainName  
    Unable to convert domain name to DNS format.  
    NamingSchemeNotEnoughCharacters  
    Naming scheme does not have enough characters specified.  
    NamingSchemeTooManyCharacters  
    Naming scheme has too many characters specified.  
    NamingSchemeIllegalCharacter  
    Naming scheme contains illegal characters.  
    NamingSchemeMayNotStartWithPeriod  
    Naming scheme starts with a period (.) character.  
    NamingSchemeMayNotBeAllNumbers  
    Naming scheme contains only numbers.  
    NamingSchemeMissingNumericSpecifications  
    Naming scheme does not contain any variable specification (i.e. no '#' characters are specified).  
    NamingSchemeHasMoreThanOneSetOfHashes  
    Naming scheme has more than one variable region (i.e. there are '#' characters separated by other characters).  
    IdentityPoolDuplicateObjectExists  
    An identity pool with the same name exists already.  
    IdentityPoolObjectNotFound  
    The identity pool to be modified could not be located.  
    IdentityPoolOUInvalid  
    Identity Pool OU invalid as it does not exist.  
    IdentityPoolOUOfWrongDomain  
    IdentityPool OU invalid as it refers to a different domain to the domain specified for the pool.  
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
C:\PS>Set-AcctIdentityPool -IdentityPoolName poolName -StartCount 100 -NamingScheme AC####
```

#### Description
Changes the start count, and the naming scheme, so that the next account generated will be AC0100 (assuming that account does not already exist)
