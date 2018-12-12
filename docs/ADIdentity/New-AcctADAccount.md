
# New-Acctadaccount
Creates AD computer accounts in the specified identity pool.
## Syntax
```
New-AcctADAccount [-IdentityPoolName] <String> -Count <Int32> [-StartCount <Int32>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AcctADAccount [-IdentityPoolName] <String> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AcctADAccount -IdentityPoolUid <Guid> -Count <Int32> [-StartCount <Int32>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AcctADAccount -IdentityPoolUid <Guid> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to create new AD computer accounts and register them in an already existing identity pool.

The accounts are created using the information stored in the identity pool. This provides the account name (via the Naming Scheme property and Start Count), domain, and OU.

The runspace used for this command must have sufficient privileges in Active Directory to create the new computer accounts.

The AD account names will pad the index to use all the space specified in the identity pool naming scheme (e.g. "acc###" will become "acc001"). However, if the index overflows the available space the cmdlet expands the format to use the next incremental number (e.g. "acc###" will become "acc1000" if the index is 10000, which cannot fit into the three '#' placeholders). If this expanded name exceeds the 15 character name limit, the accounts are not created.

There can be only one creation process running for a specific identity pool at any one time. Attempting to start another account creation process while an existing one is executing results in an error being returned.


## Related Commands

* [Add-AcctADAccount](./Add-AcctADAccount/)
* [Remove-AcctADAccount](./Remove-AcctADAccount/)
* [Get-AcctADAccount](./Get-AcctADAccount/)
* [Repair-AcctADAccount](./Repair-AcctADAccount/)
* [Unlock-AcctADAccount](./Unlock-AcctADAccount/)
* [Update-AcctADAccount](./Update-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool in which to create the accounts. | true | false |  |
| Count | The number of accounts to create. | true | false |  |
| ADAccountName | The AD account names to be created.  These are just the simple machine account names e.g. MyVM001 | true | false |  |
| IdentityPoolUid | The unique identifier for the identity pool in which the accounts will be created. | true | false |  |
| StartCount | The start index for the create process. | false | false |  |
| ADUserName | The username for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| ADPassword | The matching password for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Accountoperationdetailedsummary<br>          The Add-Acctadaccount Returns An Object That Contains The Following Parameters;<br>          Successfulaccountscount &lt;Int&gt;<br>            The Number Of Accounts That Were Added Successfully<br>          Failedaccountscount &lt;Int&gt;<br>            The Number Of Accounts That Were Not Added.<br>          Failedaccounts &lt;Citrix.Adidentity.Sdk.Accounterror\[\]&gt;<br>            The List Of Accounts That Failed To Be Added.  Each One Has The Following Parameters;<br>            Adaccountname &lt;String&gt;<br>            Adaccountsid &lt;String&gt;<br>            Errorreason &lt;String&gt;<br>            This Can Be One Of The Following<br>              Identityduplicateobjectexists<br>                An Identity With The Same Sid Already Exists.<br>              Adservicedatabaseerror<br>                  An Error Occurred In The Service While Attempting A Database Operation.<br>              Adservicedatabasenotconfigured<br>                  The Operation Could Not Be Completed Because The Database For The Service Is Not Configured.<br>              Adservicestatusinvaliddb<br>                  An Error Occurred In The Service While Attempting A Database Operation - Communication With The Database Failed For<br>                  For Various Reasons.<br>              Failedtoconnecttodomaincontroller<br>                Contacting Active Directory Failed.<br>              Failedtogetorganizationunitinad<br>                Failed To Access The Ou In Active Directory.<br>              Failedtogetdefaultcomputercontainerinad<br>                Failed To Access The Default Computers Container In Active Directory.<br>              Failedtocreatecomputeraccountinad<br>                Failed To Create The Computer Account In Active Directory.<br>              Failedtoaccesscomputeraccountinad<br>                Failed To Read The Newly Created Computer Account In Active Directory.<br>              Failedtogetsidfromad<br>                Failed To Get The Sid For The Created Account From Active Directory.<br>              Failedtosetsamaccountnameinad<br>                Failed To Set The Sam Account Name In Active Directory For The Account Created.<br>              Failedtosetuseraccountcontrolinad<br>                Failed To Set The User Account Controller Properties For The Account Created In Active Directory.<br>              Failedtosavechangeinad<br>                Failed To Save The Changes Made To The Created Computer Account In Active Directory.<br>              Failedtosetpasswordinad<br>                Failed To Set The Password For The Created Computer Account In Active Directory.<br>              Failedtoenableaccountinad<br>                Failed To Enable The Newly Created Computer Account In Active Directory.<br>              Computernamealreadyinuseinad<br>                The Computer Name For The Computer To Create Is In Use In Active Directory.<br>              Failedtogetdistinguishednameinad<br>                Failed To Get The Distinguished Name For The Created Computer Account In Activedirectory.<br>              Failedtosetdnshostnameinad<br>                Failed To Set The Dns Host Name Property For The Created Computer Account In Activedirectory.<br>              Failedtosetdisplaynameinad<br>                Failed To Set The Displayname Property For The Created Computer Account In Activedirectory.<br>              Failedtowriteserviceprincipalnameinad<br>                Failed To Set The Serviceprincipalname Property For The Created Computer Account In Activedirectory.<br>            Diagnosticinformtion &lt;Exception&gt;<br>              Any Other Error Information<br>          Successfulaccounts &lt;Citrix.Adidentity.Sdk.Identity\[\]&gt;<br>            The List Of Accounts That Were Successfully Added.  Each Object<br>            Provides Details Of The Identity And Contains The Following Information:<br>            Adaccountsid &lt;String&gt;<br>                The Sid Of The Identity.<br>            Adaccountname &lt;String&gt;<br>                      The Account Name For The Identity.<br>                      Domain &lt;String&gt;<br>                The Domain Name That The Account Was Created In.<br>            State &lt;String&gt;<br>                The Current State Of The Ad Account. This Can Be One Of The Following:<br>                Error<br>                   The Account Is Locked Or Disabled In Ad.<br>                Available<br>                   The Account Is In Ad And Available To Be Consumed By The Other Machine Creation Services.<br>                Inuse<br>                   The Account Is In Ad And Is Being Consumed By The Other Machine Creation Services.<br>                Tainted<br>                   The Account Is In Ad And No Longer Consumed By Other Machine Creation Services. However, The Password Is No Longer Known So Cannot Be Reused Without 'Repairing' The Account.  See Repair-Acctadaccount For Details.<br>            Lock &lt;Boolean&gt;<br>                Indicates If The Identity Pool Is Locked.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    NamingSchemeNotSpecifiedForIdentityPool<br>    No naming scheme is defined in the specified identity pool.<br>    IdentityPoolObjectNotFound<br>    The specified identity pool was not located.<br>    IdentityPoolAlreadyLocked<br>    The specified identity pool is locked.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>New-AcctADAccount -IdentityPoolName MyPool -Count 2 -OutVariable result

          SuccessfulAccounts                SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

          ------------------                -----------------------       -------------------    --------------

          {MyDomain\ACC001, MyDomain\ACC002} 2                            0                      {}

          $result[0].SuccessfulAccounts

          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2684

          ADAccountName : MyDomain\ACC001

          Domain        : MyDomain.com

          State         : Available

          Lock          : False

          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2685

          ADAccountName : MyDomain\ACC002

          Domain        : MyDomain.com

          State         : Available

          Lock          : False
```
#### Description
Creates two new AD accounts and registers them in the identity pool called "MyPool".
### Example 2
```
c:\PS>New-AcctADAccount -IdentityPoolName MyPool -Count 2 -StartCount 50 -OutVariable result

          SuccessfulAccounts                SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

          ------------------                -----------------------       -------------------    --------------

          {MyDomain\ACC050, MyDomain\ACC051} 2                            0                      {}

          $result[0].SuccessfulAccounts

          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2686

          ADAccountName : MyDomain\ACC050

          Domain        : MyDomain.com

          State         : Available

          Lock          : False

          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2687

          ADAccountName : MyDomain\ACC051

          Domain        : MyDomain.com

          State         : Available

          Lock          : False
```
#### Description
Creates two new AD accounts and registers them in the identity pool called "MyPool", starting from an index of 50.
