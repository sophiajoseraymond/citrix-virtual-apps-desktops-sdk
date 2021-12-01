
# New-Brokerautotagrule
Creates a new AutoTagRule.
## Syntax

```
New-BrokerAutoTagRule [-Name] <String> -ObjectType <String> -RuleText <String> -TagUid <Int32> [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
Creates an AutoTagRule which defines a rule to select objects to assign (or remove) a Tag to (or from).


## Related Commands

* [Get-BrokerAutoTagRule](../Get-BrokerAutoTagRule/)
* [Set-BrokerAutoTagRule](../Set-BrokerAutoTagRule/)
* [Remove-BrokerAutoTagRule](../Remove-BrokerAutoTagRule/)
* [Rename-BrokerAutoTagRule](../Rename-BrokerAutoTagRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | The rule name. | true | true (ByPropertyName) |  |
| ObjectType | The object type on which the rule is applied. | true | true (ByPropertyName) |  |
| RuleText | Rule in the text format. | true | true (ByPropertyName) |  |
| TagUid | The Tag Uid this rule applies to. | true | true (ByPropertyName) |  |
| Description | The Description of rule. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Autotagrule
Outputs the AutoTagRule object.
## Examples

### Example 1

```
C:\PS> $tag = New-BrokerTag -Name MyExample  
  
                    C:\PS> New-BrokerAutoTagRule -Name RandomAllocatedCatalogs -TagUid $tag.Uid -ObjectType Catalog -RuleText "-AllocationType Random"
```

#### Description
Creates a new rule for the "MyExample" tag.
