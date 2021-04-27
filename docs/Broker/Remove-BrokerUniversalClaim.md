
# Remove-Brokeruniversalclaim
Remove a Broker UniversalClaim mapping
## Syntax
```
Remove-BrokerUniversalClaim [-InputObject] <UniversalClaim[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerUniversalClaim cmdlet removes a UniversalClaim mapping that was previously added. Mappings are added automatically, and should not normally need to be removed.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the objects to be removed | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Universalclaim
You can pipe UniversalClaims to be removed by Remove-BrokerUniversalClaim
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerUniversalClaim -InputObject $ClaimToRemove
```
#### Description
Removes a UniversalClaim mapping
