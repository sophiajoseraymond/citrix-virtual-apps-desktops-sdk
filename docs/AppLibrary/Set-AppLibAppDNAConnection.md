
# Set-Applibappdnaconnection
Sets the connection details for integration of AppDNA into AppLibrary to allow AppDNA Analysis by this site.
## Syntax
```
Set-AppLibAppDNAConnection [-Address] <String> -Database <String> -UserName <String> -Password <SecureString> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Sets the connection details for integration of AppDNA into AppLibrary to allow AppDNA Analysis of AppDisk, Machines and DesktopGroups.


## Related Commands

* [Get-AppLibAppDNAConnection](./Get-AppLibAppDNAConnection/)
* [Remove-AppLibAppDNAConnection](./Remove-AppLibAppDNAConnection/)
* [Enable-AppLibAppDNAConnection](./Enable-AppLibAppDNAConnection/)
* [Deisable-AppLibAppDNAConnection](./Deisable-AppLibAppDNAConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Address | The URL to the AppDNA web server. | true | false |  |
| Database | The AppDNA database identifier. | true | false |  |
| UserName | The username of the AppDNA user to connect with. | true | false |  |
| Password | The AppDNA user's password | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### String

### System.Security.Securestring
The secure string representing the user's password.
## Return Values

### Citrix.Applibrary.Sdk.Appdnaconnection<br>                    This Object Provides Details Of The Appdna Connection And Contains The Following Information:<br>                    Address &lt;String&gt;<br>                    The Url Of The Appdna Web Server.<br>                    Database &lt;String&gt;<br>                    The Database Identifier From The Appdna Site<br>                    Enabled &lt;Bool&gt;<br>                    Whether Or Not The Connection Is Enabled<br>                    Username &lt;String&gt;<br>                    The User Account Name Used To Make The Connection.

## Notes
The AppDNA user's password is stored securely and is never returned in the AppDNAConnection object.<br>    Only one AppDNA configuration can be stored. If a connection is already set up, the connection details will be replaced.<br>    The connection will be enabled by default in the AppLibrary when the details are set.
## Examples

### Example 1
```
C:\PS>$SecurePassword = ConvertTo-SecureString -String "password" -AsPlainText -Force

                    C:\PS>Set-AppLibAppDNAConnection -Address "http://my.appdna.server:8199/AppDNA" -Database "localhost:AppDNADB" -userName "AppDNAUser" -password $SecurePassword

                    Address  : http://my.appdna.server:8199/AppDNA

                    Database : localhost:AppDNADB

                    Enabled  : True

                    UserName : AppDNAUser
```
#### Description
Sets the AppLibrary AppDNA connection to the configuration localhost:AppDNADB on my.appdna.server under the "AppDNAUser" account.
