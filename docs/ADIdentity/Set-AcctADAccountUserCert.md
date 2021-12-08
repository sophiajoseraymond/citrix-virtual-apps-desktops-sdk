
# Set-Acctadaccountusercert
Set userCertificate for the given accounts.
## Syntax

```
Set-AcctADAccountUserCert [-IdentityPoolName] <String> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-AcctADAccountUserCert [-IdentityPoolName] <String> -ADAccountSid <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-AcctADAccountUserCert [-IdentityPoolName] <String> -AllAccounts [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-AcctADAccountUserCert -IdentityPoolUid <Guid> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-AcctADAccountUserCert -IdentityPoolUid <Guid> -ADAccountSid <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Set-AcctADAccountUserCert -IdentityPoolUid <Guid> -AllAccounts [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to set userCertificate attribute for given accounts in Active Directory.


## Related Commands

* [New-AcctADAccount](../New-AcctADAccount/)
* [Add-AcctADAccount](../Add-AcctADAccount/)
* [Repair-AcctADAccount](../Repair-AcctADAccount/)
* [Unlock-AcctADAccount](../Unlock-AcctADAccount/)
* [Update-AcctADAccount](../Update-AcctADAccount/)
* [Get-AcctADAccount](../Get-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The identity pool name into which to set userCertificate of the accounts. | true | false |  |
| ADAccountName | The Active Directory account name to be set with userCertificate.  
Active Directory accounts are accepted in the following formats: Fully qualified DN e.g. CN=MyComputer,OU=Computers,DC=MyDomain,DC=Com; UPN format e.g MyComputer@MyDomain.Com; Domain qualified e.g MyDomain\\MyComputer. | true | false |  |
| ADAccountSid | The Active Directory Account SID for the account to be set with userCertificate. | true | true (ByPropertyName) |  |
| AllAccounts | Indicates if all accounts should be set with userCertificate. | true | false | false |
| IdentityPoolUid | The unique identifier for the identity pool into which to set userCertificate of the accounts. | true | true (ByPropertyName) |  |
| ADUserName | The username for an Active Directory user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| ADPassword | The matching password for an Active Directory user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| Force | Indicates if accounts that are marked as 'in-use' can be set with userCertificate. | false | false | false |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Accountoperationsummary
The Set-AcctADAccountUserCert command returns an object with the following parameters:  
    SuccessfulAccountsCount &lt;int&gt;  
        The number of accounts that were successfully set with userCertificate.  
    FailedAccountsCount &lt;int&gt;  
        The number of accounts that were failed to set with userCertificate.  
    FailedAccounts &lt;Citrix.ADIdentity.Sdk.AccountError\[\]&gt;  
        The list of accounts that failed to be set with userCertificate. Each one has the following parameters:  
            ADAccountName &lt;string&gt;  
            ADAccountSid &lt;String&gt;  
            ErrorReason &lt;ADIdentityStatus&gt;  
              This can be one of the following:  
                IdentityObjectNotFound  
                IdentityObjectLocked  
                IdentityObjectInUse  
                IdentityPoolObjectNotFound  
                ADServiceDatabaseError  
                ADServiceDatabaseNotConfigured  
                ADServiceStatusInvalidDb  
                FailedToConnectToDomainController  
                FailedToGenerateDeviceKeyPair  
                FailedToAccessComputerAccountInAD  
            DiagnosticInformation &lt;Exception&gt;  
                Any other error information
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation - communication with database failed for  
    various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Set-AcctADAccountUserCert -IdentityPoolName MyPool -ADAccountName "Domain\account","Domain\account2"  
  
          SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts  
  
          -----------------------       -------------------    --------------  
  
          2                         0    {}
```

#### Description
Set userCertificate for two accounts (account and account2) in the identity pool called "MyPool".
### Example 2

```
C:\PS>Set-AcctADAccountUserCert -IdentityPoolName MyPool -ADAccountName "Domain\account","Domain\account2" -Force  
  
            SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts  
  
            -----------------------       -------------------    --------------  
  
            2                         0    {}
```

#### Description
Set userCertificate for two accounts (account and account2) in the identity pool called "MyPool". The accounts are set regardless of whether they are in the 'inUse' state or not.
### Example 3

```
C:\PS>Set-AcctADAccountUserCert -IdentityPoolName MyPool -ADAccountName "Domain\account","Domain\account2" -OutVariable result  
  
            SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts  
  
            -----------------------       -------------------    --------------  
  
            1                                               1    {account2}  
  
            C:\PS>$result[0].FailedAccounts  
  
          ADAccountName                 ADAccountSid           ErrorReason  
  
          -------------                 -------------          ------------  
  
          Domain\account2               account2               IdentityObjectLocked
```

#### Description
Shows failure of setting of one of two accounts and how to retrieve the failure reason.
### Example 4

```
C:\PS>Set-AcctADAccountUserCert -IdentityPoolName MyPool -ADAccountSid S-1-5-21-1315084875-1285793635-2418178940-2685  
  
            SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts  
  
            -----------------------       -------------------    --------------  
  
            1                                               0    {}
```

#### Description
Set userCertificate for one account (S-1-5-21-1315084875-1285793635-2418178940-2685) in the identity pool called "MyPool".
