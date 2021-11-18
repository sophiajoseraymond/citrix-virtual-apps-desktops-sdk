
# New-Acctidentitypool
Creates a new identity pool.
## Syntax

```
New-AcctIdentityPool -IdentityPoolName <String> [-OU <String>] [-Domain <String>] [-NamingScheme <String>] [-NamingSchemeType <ADIdentityNamingScheme>] [-AllowUnicode] [-StartCount <Int32>] [-Scope <String[]>] [-TenantId <Guid>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
New-AcctIdentityPool -WorkgroupMachine -IdentityPoolName <String> [-NamingScheme <String>] [-NamingSchemeType <ADIdentityNamingScheme>] [-AllowUnicode] [-StartCount <Int32>] [-Scope <String[]>] [-TenantId <Guid>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to create identity pools that can be used to store AD computer accounts.

The naming scheme, naming scheme type, and domain must be specified if the identity pool is to be used to create new accounts.

Each identity pool is tied to a single domain. All the identities in an identity pool belong to the same domain. If the domain is not specified by a parameter to this command the domain will be set when an account is imported into it.


## Related Commands

* [Remove-AcctIdentityPool](../Remove-AcctIdentityPool/)
* [Rename-AcctIdentityPool](../Rename-AcctIdentityPool/)
* [Set-AcctIdentityPool](../Set-AcctIdentityPool/)
* [Test-AcctIdentityPoolNameAvailable](../Test-AcctIdentityPoolNameAvailable/)
* [New-AcctADAccount](../New-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool.  This must not contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | false |  |
| WorkgroupMachine | If the accounts created should be is be part of a workgroup rather than a domain | true | false |  |
| NamingScheme | Defines the template name for AD accounts created in the identity pool.  The scheme can consist of fixed characters and a variable part defined by '#' characters.  There can be only one variable region defined. The number of '#' characters defines the minimum length of the variable region. For example, a naming scheme of H#### could create accounts called H0001, H0002 (for a numeric scheme type) or HAAAA, HAAAB (for an alphabetic type).  
Citrix recommends that you define a naming scheme that will not clash with accounts which already exist in AD; account creation will fail if a clash occurs.  
There are restrictions on what constitutes a valid computer name: Minimum name length: 2 (DNS) Maximum name length: 15 bytes (NetBIOS) The following characters are not allowed in a computer name: backslash (\\) slash mark (/) colon (:) asterisk (\*) question mark (?) quotation mark (") less than sign (&lt;) greater than sign (&gt;) vertical bar (|) comma (,) tilde (~) exclamation point (!) at sign (@) number sign (#) dollar sign (\$) percent (%) caret (^) ampersand (&) apostrophe (') parenthesis (()) braces ({}) underscore (\_) The following names are reserved and must not be used at the end of the naming scheme: -GATEWAY -GW -TAC Names must not start with a period (NetBIOS). Names must not be composed entirely of numbers (NetBIOS). Names must not contain a blank or space characters (DNS). | false | false |  |
| NamingSchemeType | The type of naming scheme.  This can be Numeric or Alphabetic.  This defines the format of the variable part of the AD account names that will be created. | false | false | Numeric |
| AllowUnicode | Allow the naming scheme to have characters other than alphanumeric characters. | false | false |  |
| StartCount | Defines the next number that will be used if creating new AD accounts for the identity pool. | false | false |  |
| Scope | The administration scopes to be applied to the new identity pool. | false | false |  |
| TenantId | Specifies identity of tenant associated with Identity Pool. Must always be specified in multitenant sites, must not be specified otherwise. | false | false |  |
| ZoneUid | The UID that corresponds to the Zone in which these AD accounts will be created. This is only intended to be used for Citrix Cloud Delivery Controllers. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |
| OU | The OU that computer accounts will be created into. If this is not specified, accounts are created into the default account container specified by AD.  This is the 'Computers' container for out-of-the-box installations of AD.  The OU must be a valid AD container and of the domain specified for the pool; | false | false |  |
| Domain | The AD domain name for the pool.  Specify this in FQDN format; for example, MyDomain.com. | false | false |  |

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
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
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
    An identity pool with the same name already exists.  
    IdentityPoolOUInvalid  
    Identity Pool OU invalid as it does not exist.  
    IdentityPoolOUOfWrongDomain  
    IdentityPool OU invalid as it refers to a different domain to the domain specified for the pool.  
    InvalidIdentityPoolParameterCombination  
    Caused by either of the following validation errors:  
    \* If an OU is specified then a domain must also be specified.  
    \* NamingScheme, NamingSchemeType and Domain must all be present if any of these are specified.  
    NamingSchemeIllegalComputerName  
    The naming scheme supplied is not valid.  
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
c:\PS>New-AcctIdentityPool -IdentityPoolName MyPool -NamingScheme Acc#### -Domain MyDomain.com -NamingSchemeType Numeric  
  
IdentityPoolName : MyPool  
  
IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915  
  
NamingScheme     : Acc####  
  
NamingSchemeType : Numeric  
  
StartCount       : 1  
  
OU               :  
  
Domain           : MyDomain.com  
  
Lock             : False
```

#### Description
Create a new identity pool from which accounts can be created in the domain called "MyDomain.com" using a numeric scheme of the format Acc####.  The first account that will be created from this identity pool definition is Acc0001.  
New AD accounts can be imported into this pool too, but must be from the Domain "MyDomain.com".
