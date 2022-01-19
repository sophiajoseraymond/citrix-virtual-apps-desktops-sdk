
# Get-Brokerautotagrule
Gets AutoTagRules that have been defined for this site.
## Syntax

```
Get-BrokerAutoTagRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Get-BrokerAutoTagRule [[-Name] <String>] [-Description <String>] [-Metadata <String>] [-ObjectType <String>] [-RuleText <String>] [-TagUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
Retrieves AutoTagRules matching the specified criteria. If no parameters are specified this cmdlet enumerates all catalogs.

See [about\_Broker\_Filtering](../about_Broker_Filtering/) for information about advanced filtering options.


### Brokerautotagrule Object
The BrokerAutoTagRule object represents a single instance of an AutoTagRule.

See about\_Broker\_AutoTagRule for more information.

A BrokerAutoTagRule contains the following properties:


  * Description (System.String) Description of the AutoTagRule

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) The metadata for the AutoTagRule.

  * Name (System.String) The name of the AutoTagRule

  * ObjectType (System.String) The object type the rule is applied to.

  * RuleText (System.String) The rule in a text format

  * TagUid (System.Int32) The Tag Uid this rule sets or removes

  * Uid (System.Int32) The Uid of the AutoTagRule


## Related Commands

* [New-BrokerAutoTagRule](../New-BrokerAutoTagRule/)
* [Set-BrokerAutoTagRule](../Set-BrokerAutoTagRule/)
* [Remove-BrokerAutoTagRule](../Remove-BrokerAutoTagRule/)
* [Rename-BrokerAutoTagRule](../Rename-BrokerAutoTagRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the AutoTagRule with the unique identifier. | true | false |  |
| Name | Gets AutoTagRules that have the specified name. | false | false |  |
| Description | Gets the AutoTagRules that have the specified Description. | false | false |  |
| Metadata | Gets records with matching metadata entries.  
The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| ObjectType | Gets the AutoTagRules that operate on the ObjectType. | false | false |  |
| RuleText | Gets the AutoTagRules that have the specified RuleText. | false | false |  |
| TagUid | Gets the AutoTagRule associated with the TagUid. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See [about\_Broker\_Filtering](../about_Broker_Filtering/) for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See [about\_Broker\_Filtering](../about_Broker_Filtering/) for details. | false | false |  |
| FilterScope | Gets only results allowed by the specified scope id. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Autotagrule
Get-AutoTagRule returns matching AutoTagRule objects.
## Examples

### Example 1

```
C:\PS> Get-AutoTagRule -Name RandomAllocatedCatalogs
```

#### Description
Gets the AutoTagRules with the name RandomAllocatedCatalogs
