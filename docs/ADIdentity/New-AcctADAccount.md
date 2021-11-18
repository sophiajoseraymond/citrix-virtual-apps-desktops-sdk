
# New-Acctadaccount
Creates AD computer accounts in the specified identity pool.
## Syntax

```
New-AcctADAccount [-IdentityPoolName] <String> -Count <Int32> [-StartCount <Int32>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
New-AcctADAccount [-IdentityPoolName] <String> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
New-AcctADAccount -IdentityPoolUid <Guid> -Count <Int32> [-StartCount <Int32>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
New-AcctADAccount -IdentityPoolUid <Guid> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to create new AD computer accounts and register them in an already existing identity pool.

The accounts are created using the information stored in the identity pool. This provides the account name (via the Naming Scheme property and Start Count), domain, and OU.

The runspace used for this command must have sufficient privileges in Active Directory to create the new computer accounts.

The AD account names will pad the index to use all the space specified in the identity pool naming scheme (e.g. "acc###" will become "acc001"). However, if the index overflows the available space the cmdlet expands the format to use the next incremental number (e.g. "acc###" will become "acc1000" if the index is 10000, which cannot fit into the three '#' placeholders). If this expanded name exceeds the 15 character name limit, the accounts are not created.

There can be only one creation process running for a specific identity pool at any one time. Attempting to start another account creation process while an existing one is executing results in an error being returned.


## Related Commands

* [Add-AcctADAccount](../Add-AcctADAccount/)
* [Remove-AcctADAccount](../Remove-AcctADAccount/)
* [Get-AcctADAccount](../Get-AcctADAccount/)
* [Repair-AcctADAccount](../Repair-AcctADAccount/)
* [Unlock-AcctADAccount](../Unlock-AcctADAccount/)
* [Update-AcctADAccount](../Update-AcctADAccount/)
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
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Accountoperationdetailedsummary
The Add-AcctADAccount returns an object that contains the following parameters;  
          SuccessfulAccountsCount &lt;int&gt;  
            The number of accounts that were added successfully  
          FailedAccountsCount &lt;int&gt;  
            The number of accounts that were not added.  
          FailedAccounts &lt;Citrix.ADIdentity.Sdk.AccountError\[\]&gt;  
            The list of accounts that failed to be added.  Each one has the following parameters;  
            ADAccountName &lt;string&gt;  
            ADAccountSid &lt;String&gt;  
            ErrorReason &lt;string&gt;  
            This can be one of the following  
              IdentityDuplicateObjectExists  
                An identity with the same SID already exists.  
              ADServiceDatabaseError  
                  An error occurred in the service while attempting a database operation.  
              ADServiceDatabaseNotConfigured  
                  The operation could not be completed because the database for the service is not configured.  
              ADServiceStatusInvalidDb  
                  An error occurred in the service while attempting a database operation - communication with the database failed for  
                  for various reasons.  
              FailedToConnectToDomainController  
                Contacting Active Directory failed.  
              FailedToGetOrganizationUnitInAD  
                Failed to access the OU in Active Directory.  
              FailedToGetDefaultComputerContainerInAD  
                Failed to access the default computers container in Active Directory.  
              FailedToCreateComputerAccountInAD  
                Failed to create the computer account in Active Directory.  
              FailedToAccessComputerAccountInAD  
                Failed to read the newly created computer account in Active Directory.  
              FailedToGetSidFromAD  
                Failed to get the SID for the created account from Active Directory.  
              FailedToSetSamAccountNameInAD  
                Failed to set the SAM account name in Active Directory for the account created.  
              FailedToSetUserAccountControlInAD  
                Failed to set the user account controller properties for the account created in Active Directory.  
              FailedToSaveChangeInAD  
                Failed to save the changes made to the created computer account in Active Directory.  
              FailedToSetPasswordInAD  
                Failed to set the password for the created computer account in Active Directory.  
              FailedToEnableAccountInAD  
                Failed to enable the newly created computer account in Active Directory.  
              ComputerNameAlreadyInUseInAD  
                The computer name for the computer to create is in use in Active Directory.  
              FailedToGetDistinguishedNameInAD  
                Failed to get the distinguished name for the created computer account in ActiveDirectory.  
              FailedToSetDnsHostNameInAD  
                Failed to set the Dns Host Name property for the created computer account in ActiveDirectory.  
              FailedToSetDisplayNameInAD  
                Failed to set the DisplayName property for the created computer account in ActiveDirectory.  
              FailedToWriteServicePrincipalNameInAD  
                Failed to set the ServicePrincipalName property for the created computer account in ActiveDirectory.  
            DiagnosticInformtion &lt;Exception&gt;  
              Any other error information  
          SuccessfulAccounts &lt;Citrix.ADIdentity.Sdk.Identity\[\]&gt;  
            The list of accounts that were successfully added.  Each object  
            provides details of the identity and contains the following information:  
            ADAccountSID &lt;string&gt;  
                The Sid of the identity.  
            ADAccountName &lt;string&gt;  
                      The account name for the identity.  
                      Domain &lt;string&gt;  
                The domain name that the account was created in.  
            State &lt;string&gt;  
                The current state of the AD account. This can be one of the following:  
                Error  
                   The account is locked or disabled in AD.  
                Available  
                   The account is in AD and available to be consumed by the other Machine Creation Services.  
                InUse  
                   The account is in AD and is being consumed by the other Machine Creation Services.  
                Tainted  
                   The account is in AD and no longer consumed by other Machine Creation Services. However, the password is no longer known so cannot be reused without 'Repairing' the account.  See repair-AcctADAccount for details.  
            Lock &lt;Boolean&gt;  
                Indicates if the identity pool is locked.
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    NamingSchemeNotSpecifiedForIdentityPool  
    No naming scheme is defined in the specified identity pool.  
    IdentityPoolObjectNotFound  
    The specified identity pool was not located.  
    IdentityPoolAlreadyLocked  
    The specified identity pool is locked.  
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
