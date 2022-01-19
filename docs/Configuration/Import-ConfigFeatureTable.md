
# Import-Configfeaturetable
Sets the feature table of a site. This cmdlet can also be used to apply extra partial feature table files supplied by Citrix as needed to enable specific features. The XML feature table file is a signed file which Citrix provides for specific use cases on request.
## Syntax

```
Import-ConfigFeatureTable [-Path] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Import-ConfigFeatureTable -Content <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description



## Related Commands

* [Export-ConfigFeatureTable](../Export-ConfigFeatureTable/)
* [Get-ConfigSite](../Get-ConfigSite/)
* [Set-ConfigSite](../Set-ConfigSite/)
* [Get-ConfigProduct](../Get-ConfigProduct/)
* [Get-ConfigProductEdition](../Get-ConfigProductEdition/)
* [Get-ConfigProductFeature](../Get-ConfigProductFeature/)
* [Get-ConfigProductVersion](../Get-ConfigProductVersion/)
* [Get-ConfigLicensingModel](../Get-ConfigLicensingModel/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Path | The path to the file containing the feature table | true | false |  |
| Content | Set the site's feature table. (Can also update existing feature table by adding feature table fragments for specific extra features) | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. Once a value is provided by any cmdlet, this value becomes the default. | false | false |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1

```
C:\PS> Import-ConfigFeatureTable -Path "XML_FeatureTable_File_Path\FeatureTableFilename.xml"
```

#### Description
Imports a feature table by specifying the path to a signed XML file provided by Citrix.
