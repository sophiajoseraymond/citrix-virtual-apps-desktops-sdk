
# Set-Brokerautotagrule
Changes an existing AutoTagRule.
## Syntax

```
Set-BrokerAutoTagRule [-InputObject] <AutoTagRule[]> [-PassThru] [-Description <String>] [-ObjectType <String>] [-RuleText <String>] [-TagUid <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Set-BrokerAutoTagRule [-Name] <String> [-PassThru] [-Description <String>] [-ObjectType <String>] [-RuleText <String>] [-TagUid <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
Changes the specified properties of an existing AutoTagRule.


## Related Commands

* [Get-BrokerAutoTagRule](../Get-BrokerAutoTagRule/)
* [New-BrokerAutoTagRule](../New-BrokerAutoTagRule/)
* [Remove-BrokerAutoTagRule](../Remove-BrokerAutoTagRule/)
* [Rename-BrokerAutoTagRule](../Rename-BrokerAutoTagRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the AutoTagRule object to change. | true | true (ByValue) |  |
| Name | The name of the AutoTagRule to change. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Description | New Description that will be set. | false | false |  |
| ObjectType | New ObjectType that will be set. | false | false |  |
| RuleText | New RuleText that will be set. | false | false |  |
| TagUid | New TagUid that will be set. | false | false |  |
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
C:\PS> $tag = New-BrokerTag -Name MyExample2  
  
C:\PS> Set-BrokerAutoTagRule -Name RandomAllocatedCatalogs -TagUid $tag.Uid
```

#### Description
Sets RandomAllocatedCatalogs' tag to MyExample2.
