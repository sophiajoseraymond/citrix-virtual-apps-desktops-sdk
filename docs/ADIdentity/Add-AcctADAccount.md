
# Add-Acctadaccount
Import Active Directory computer accounts from Active Directory for use in the AD Identity Service.
## Syntax

```
Add-AcctADAccount [-IdentityPoolName] <String> -ADAccountName <String[]> [-Password <String>] [-SecurePassword <SecureString>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Add-AcctADAccount -IdentityPoolUid <Guid> -ADAccountName <String[]> [-Password <String>] [-SecurePassword <SecureString>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability for Active Directory computer accounts that already exist in Active Directory to be used by the Citrix AD Identity Service and the other Citrix Machine Creation Services.

All aspects of this command that need to make modifications to the accounts in Active Directory will do so using the account that the PowerShell runspace is using.  This means that if the passwords need resetting for the accounts, the user performing the operation in PowerShell must have sufficient privileges in Active Directory for this operation to complete successfully.

The following rules apply to the importing of Active Directory accounts; If the current account password is supplied, the cmdlet will attempt to change the password so that it is known only to the Citrix Identity Service.  This uses password change operations and does not need AD account administration permissions. If the current password is not supplied, the cmdlet will attempt to reset the password for the Active Directory account so that it is known only to the Citrix Identity Service. This requires the cmdlet to have enough privileges in Active Directory for the accounts' password reset to be available. Imported accounts in a disabled or locked state in Active Directory are imported with the account marked in an error state. If the identity pool into which the account is being imported does not have a domain set, it assumes the domain of the first account imported into it.


## Related Commands

* [New-AcctADAccount](../New-AcctADAccount/)
* [Remove-AcctADAccount](../Remove-AcctADAccount/)
* [Repair-AcctADAccount](../Repair-AcctADAccount/)
* [Get-AcctADAccount](../Get-AcctADAccount/)
* [Update-AcctADAccount](../Update-AcctADAccount/)
* [Unlock-AcctADAccount](../Unlock-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The identity pool name into which to add the imported accounts. | true | true (ByPropertyName) |  |
| ADAccountName | The Active Directory account name to be imported.  
Active Directory accounts are accepted in the following formats: Fully qualified DN e.g. CN=MyComputer,OU=Computers,DC=MyDomain,DC=Com; UPN format e.g MyComputer@MyDomain.Com; Domain qualified e.g MyDomain\\MyComputer. | true | false |  |
| IdentityPoolUid | The unique identifier for the identity pool to which imported accounts are to be added. | true | true (ByPropertyName) |  |
| Password | The current password for the computer account. | false | false |  |
| SecurePassword | The current password for the account (provided in a Secure String class). | false | false |  |
| ADUserName | The username for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| ADPassword | The matching password for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Accountoperationdetailedsummary
The Add-AcctADAccount returns an object that contains the following parameters;  
          SuccessfulAccountsCount &lt;int&gt;  
            The number of accounts that were added successfully  
          FailedAccountsCount &lt;int&gt;  
            The number of accounts that were not added.  
          FailedAccounts &lt;Citrix.XDPowerShell.AccountError\[\]&gt;  
            The list of accounts that failed to be added.  Each one has the following properties;  
              ADAccountName &lt;string&gt;  
              ADAccountSid &lt;String&gt;  
            ErrorReason &lt;ADIdentityStatus&gt;  
              This can be one of the following  
                  UnableToConvertDomain  
                  UnableToAccessAccountProperties  
                  IdentityNotLocatedInDomain  
                  UnableToAccessAccountProperties  
                  IdentityDuplicateObjectExists  
                  IdentityObjectLocked  
                  IdentityObjectInUse  
                  FailedToConnectToDomainController  
                  FailedToExecuteSearchInAD  
                  FailedToAccessComputerAccountInAD  
                  FailedToSetPasswordInAD  
                  FailedToChangePasswordInAD  
                  ADServiceDatabaseError  
                  ADServiceDatabaseNotConfigured  
                  ADServiceStatusInvalidDb  
            DiagnosticInformtion &lt;Exception&gt;  
                Any other error information  
          SuccessfulAccounts &lt;Citrix.ADIdentity.Sdk.Identity\[\]&gt;  
            The list of accounts that were successfully added.  Each one has the following properties;  
            ADAccountSid &lt;string&gt;  
              The AD account SID for the imported account.  
            ADAccountName &lt;string&gt;  
              The AD account name for the imported account.  
            Domain &lt;string&gt;  
              The domain for the imported account.  
            State &lt;Citrix.ADIdentity.Sdk.ADIdentityState&gt;  
              The state for the account. This can be;  
                Available  
                    The account is not used.  
                InUse  
                    The account is in use.  
                Error  
                    The account is in error (i.e. the account is locked or disabled in AD).  
                Tainted  
                     The account is no longer used, but the password is no longer known.  
            Lock &lt;Boolean&gt;  
              The account is locked (in the database not in AD).
## Notes
To maintain maximum security when using the command programmatically, Citrix recommends you use the 'SecurePassword' property instead of the 'Password' property.  
    In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    IdentityPoolAlreadyLocked  
    The specified identity pool was locked by another operation.  
    IdentityPoolNotFound  
    The specified identity pool was not found.  
    IdentityDuplicateObjectExists  
    The specified AD account already exists for the identity pool.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Add-AcctADAccount -IdentityPoolName MyPool -ADAccountName "Domain\account","Domain\account2" -OutVariable result  
  
  SuccessfulAccounts                SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts  
  
  ------------------                -----------------------       -------------------    --------------  
  
  {domain\account, domain\account2} 2                            0                      {}  
  
          $result[0].SuccessfulAccounts  
  
          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2644  
  
          ADAccountName : domain\account  
  
          Domain        : Domain.com  
  
          State         : Available  
  
          Lock          : False  
  
          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2645  
  
          ADAccountName : domain\account2  
  
          Domain        : Domain.com  
  
          State         : Available  
  
          Lock          : False
```

#### Description
Import the two accounts (account and account2) from AD into the identity Pool called "MyPool"
