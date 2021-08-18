
# Unpublish-Provmastervmimage
Remove a prepared master image from the provisioning scheme.
## Syntax
```
Unpublish-ProvMasterVMImage [-ProvisioningSchemeName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Unpublish-ProvMasterVMImage -ProvisioningSchemeUid <Guid> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Unpublish-ProvMasterVMImage -VMImageHistoryUid <Guid> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to remove a hard disk image that has been prepared to provision virtual machines.

A background task will be created to remove the old hard disk copies.  You can locate and monitor this task using the Get-ProvTask cmdlet.

The affected hard disk image is removed from the history (see Get-ProvSchemeMasterVMImageHistory).


## Related Commands

* [New-ProvMasterVMImage](../New-ProvMasterVMImage/)
* [Get-ProvSchemeMasterVMImageHistory](../Get-ProvSchemeMasterVMImageHistory/)
* [Get-ProvScheme](../Get-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The provisioning scheme from which the surplus hard disk images should be removed. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The provisioning scheme identifier from which the surplus hard disk images should be removed. | true | false |  |
| VMImageHistoryUid | The specific master image for which hard disk images should be removed. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Notes
If a VM Image History UID is specified, the cmdlet will remove the image if it is in the prepared state. If the image is the current image of the provisioning scheme, an error will be returned: there must be a current image associated with a provisioning scheme. The Publish-ProvMasterVMImage cmdlet may be used to replace a current image with a new or previously prepared image.<br>    If a provisioning scheme name or UID is specified, the cmdlet will remove the prepared master image associated with that provisioning scheme, if it exists. No error will be returned if no prepared image exists. The current image of the scheme will not be removed.
## Examples

### Example 1
```
c:\PS>Unpublish-ProvMasterVMImage -ProvisioningSchemeName MyScheme
```
#### Description
Removes the prepared master hard disk image for the provisioning Scheme "MyScheme".
### Example 2
```
c:\PS>Unpublish-ProvMasterVMImage -VMImageHistoryUid 7585f0de-192e-4847-a6d8-22713c3a2f42 -Revoke
```
#### Description
Removes a prepared image identified by its history record.
