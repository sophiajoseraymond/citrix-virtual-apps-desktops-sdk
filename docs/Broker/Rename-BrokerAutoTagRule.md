
# Rename-Brokerautotagrule
Renames the AutoTagRule.
## Syntax

```
Rename-BrokerAutoTagRule [-InputObject] <AutoTagRule[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Rename-BrokerAutoTagRule [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
Renames the AutoTagRule.


## Related Commands

* [Get-BrokerAutoTagRule](../Get-BrokerAutoTagRule/)
* [New-BrokerAutoTagRule](../New-BrokerAutoTagRule/)
* [Set-BrokerAutoTagRule](../Set-BrokerAutoTagRule/)
* [Remove-BrokerAutoTagRule](../Remove-BrokerAutoTagRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the AutoTagRule object to rename. | true | true (ByValue) |  |
| Name | Specifies the AutoTagRule be renamed. | true | true (ByPropertyName) |  |
| NewName | Specifies the new name for the AutoTagRule. | true | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Autotagrule
AutoTagRule may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1

```
C:\PS> Rename-BrokerAutoTagRule -Name RandomAllocatedCatalogs -NewName StaticAllocatedCatalogs
```

#### Description
Renames RandomAllocatedCatalogs to StaticAllocatedCatalogs.
