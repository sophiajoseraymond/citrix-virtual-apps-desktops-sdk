
# Export-Provscheme
Exports a provisioning scheme in the form of a JSON encoded string
## Syntax

```
Export-ProvScheme -ProvisioningSchemeName <String> [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Export-ProvScheme -ProvisioningSchemeUid <Guid> [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
The primary use of this cmdlet to export an provisioning scheme and the VM that are part of the provisioning scheme the exported JSON can then be used to import this provisioning scheme into different sites.


The exported provisioning scheme contains the provisioning scheme, provisioned VMs, Image history.


however it does not contain the AD Account, use the Cmdlet Export-AcctIdentityPool to export the Indentity pool


## Related Commands

* [Import-ProvScheme](../Import-ProvScheme/)
* [Export-AcctIdentityPool](../Export-AcctIdentityPool/)
* [Import-AcctIdentityPool](../Import-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | true | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.String
A JSON encoded version of the provisioning scheme and the VMs that are part of the provisioning scheme
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    ProvisioningSchemeNotFound  
    The specified provisioning scheme could not be located.
## Examples

### Example 1

```
C:\PS> Export-ProvScheme -ProvisioningSchemeName MyScheme
```

#### Description
Exports the provisioning scheme with the name MyScheme
