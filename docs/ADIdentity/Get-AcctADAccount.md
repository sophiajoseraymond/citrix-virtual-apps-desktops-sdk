
# Get-Acctadaccount
Gets the AD accounts stored in the AD Identity Service.
## Syntax
```
Get-AcctADAccount [-IdentityPoolName <String>] [-ADAccountSid <String>] [-Domain <String>] [-State <ADIdentityState>] [-Lock <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Get-AcctADAccount [-IdentityPoolUid <Guid>] [-ADAccountSid <String>] [-Domain <String>] [-State <ADIdentityState>] [-Lock <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to locate the AD accounts stored within the AD Identity Service and view the state of the accounts.


## Related Commands

* [New-AcctADAccount](./New-AcctADAccount/)
* [Add-AcctADAccount](./Add-AcctADAccount/)
* [Remove-AcctADAccount](./Remove-AcctADAccount/)
* [Unlock-AcctADAccount](./Unlock-AcctADAccount/)
* [Update-AcctADAccount](./Update-AcctADAccount/)
* [Repair-AcctADAccount](./Repair-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ADAccountSid | The AD Account SID of the account. | false | false |  |
| Domain | The domain of the account (this is in dns format). | false | false |  |
| State | The current state of the identity stored in the AD Identity Service for the AD account. | false | false |  |
| Lock | Indicates if the account is locked in the AD Identity Service. | false | false |  |
| ReturnTotalRecordCount | See about\_Acct\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Acct\_Filtering for details. | false | false | 250 |
| Skip | See about\_Acct\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Acct\_Filtering for details. | false | false |  |
| Filter | See about\_Acct\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |
| IdentityPoolName | The name of the identity pool to which the account is registered. | false | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool that the account is registered to. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Identityinpool<br>    The Get-Acctadaccount Returns An Object That Contains The Following Parameters<br>        Adaccountsid &lt;String&gt;<br>            The Ad Account Sid For The Retrieved Account.<br>        Adaccountname &lt;String&gt;<br>          The Ad Account Name For The Retrieved Account.<br>          Domain &lt;String&gt;<br>            The Domain For The Imported Account.<br>        State &lt;Citrix.Xdinterservicetypes.Adidentitystate&gt;<br>            The State For The Account. This Can Be;<br>                Available<br>                    The Account Is Not Used.<br>                Inuse<br>                    The Account Is In Use.<br>                Error<br>                    The Account Is In Error (I.E. The Account Is Locked Or Disabled In Ad).<br>                Tainted<br>                     The Account Is No Longer Used, But The Password Is No Longer Known.<br>        Lock &lt;Boolean&gt;<br>            The Account Is Locked (In The Database Not In Ad).<br>        Identitypoolname &lt;System.String&gt;<br>            The Name Of The Containing Identity Pool.<br>        Identitypooluid &lt;System.Guid&gt;<br>            The Guid Identifying The Containing Identity Pool.

## Notes
In the case of failure the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\>Get-AcctADAccount
```
#### Description
Return all the AD accounts that are registered in the AD Identity Service.
### Example 2
```
C:\>Get-AcctADAccount -IdentityPoolName MyPool -Lock $false
```
#### Description
Return all the AD accounts that are registered in the AD Identity Service in the identity pool called "MyPool" that are also locked.
### Example 3
```
C:\>Get-AcctADAccount -Filter {IdentityPoolName -Like "p\*" -or IdentityPoolName -eq "MyPool"}
```
#### Description
Return all the AD accounts that are registered in the AD Identity Service in the identity pool called "MyPool" or in an identity pool that has a name that starts with a 'p'.  For full details of the advanced filtering aspects of this command see about\_Acct\_Filtering.
