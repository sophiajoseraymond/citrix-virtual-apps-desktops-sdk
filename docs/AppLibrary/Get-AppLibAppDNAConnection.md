
# Get-Applibappdnaconnection
Gets the AppDNA connection details.
## Syntax
```
Get-AppLibAppDNAConnection [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Gets the AppDNA Connection details used to integrate Citrix Studio with AppDNA.


## Related Commands

* [Set-AppLibAppDNAConnection](../Set-AppLibAppDNAConnection/)
* [Remove-AppLibAppDNAConnection](../Remove-AppLibAppDNAConnection/)
* [Enable-AppLibAppDNAConnection](../Enable-AppLibAppDNAConnection/)
* [Disable-AppLibAppDNAConnection](../Disable-AppLibAppDNAConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appdnaconnection<br>                    This Object Provides Details Of The Appdna Connection And Contains The Following Information:<br>                    Address &lt;String&gt;<br>                    The Url Of The Appdna Web Server.<br>                    Database &lt;String&gt;<br>                    The Database Identifier From The Appdna Site<br>                    Enabled &lt;Bool&gt;<br>                    Whether Or Not The Connection Is Enabled<br>                    Username &lt;String&gt;<br>                    The User Account Name Used To Make The Connection.

## Notes
The AppDNA user's password is never returned with the connection details.
## Examples

### Example 1
```
C:\PS>Get-AppLibAppDNAConnection

                    Address  : http://AppDNAServer.mynetwork.net:8199/AppDNA

                    Database : AppDNAServer:AppDNADB

                    Enabled  : True

                    UserName : AppDNAUser
```
#### Description
Gets the AppDNA Connection details used to integrate Citrix Studio with AppDNA.
