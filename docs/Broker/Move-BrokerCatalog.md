
# Move-Brokercatalog
Move a published catalog from one admin folder to another
## Syntax

```
Move-BrokerCatalog [-InputObject] <Catalog[]> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Move-BrokerCatalog [-Name] <String> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
The Move-BrokerCatalog cmdlet moves a published catalog from one place to another in the tree of admin folders, optionally renaming it in the process (if you only want to change the name of the catalog for administrative purposes and not its location in the tree, use the Rename-BrokerCatalog cmdlet).

The location and name of a published catalog in this sense is only of interest to the administrator, changes do not affect the end-user experience.


## Related Commands

* [Get-BrokerCatalog](../Get-BrokerCatalog/)
* [New-BrokerCatalog](../New-BrokerCatalog/)
* [Remove-BrokerCatalog](../Remove-BrokerCatalog/)
* [Move-BrokerCatalog](../Move-BrokerCatalog/)
* [Rename-BrokerCatalog](../Rename-BrokerCatalog/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The catalog(s) to be moved | true | true (ByValue) |  |
| Name | The name of the catalog to be moved | true | true (ByPropertyName) |  |
| Destination | The destination location within the admin folder hierarchy. | true | false |  |
| NewName | The new name of the catalog in its new destination | false | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Catalog
You can pipe catalogs to Move-BrokerCatalog.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Catalog
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Catalog object.
