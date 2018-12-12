
# Remove-Provscheme
Removes a provisioning scheme
## Syntax
```
Remove-ProvScheme [-ProvisioningSchemeName] <String> [-ForgetVM] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ProvScheme -ProvisioningSchemeUid <Guid> [-ForgetVM] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to remove a provisioning Scheme.  The provisioning scheme must not contain any VMs unless the 'ForgetVM' option is specified.

If 'ForgetVM' is not specified, a cmdlet task is created that runs in the background to remove the hard disk copies that have been created for the provisioning scheme in hypervisor storage.  Use the Get-ProvTask command to monitor the progress of this task.


## Related Commands

* [Get-ProvTask](./Get-ProvTask/)
* [New-ProvScheme](./New-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme to be removed. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme to be removed. | true | true (ByPropertyName) |  |
| ForgetVM | Indicates whether or not the VMs in the provisioning scheme should be left in the hypervisor and only the data held in the Machine Creation Services removed.  If this is specified, it is up to the administrator of the hypervisor to remove the VMs and hard disk images using the tools provided by the hypervisor itself. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme<br>    This Object Provides Details Of The Provisioning Scheme And Contains The Following Information:<br>    Provisioningschemeuid<br>        The Unique Identifier For The Provisioning Scheme.<br>    Provisioningschemename<br>        The Name Of The Provisioning Scheme.<br>    Cpucount<br>        The Number Of Processors That Vms Will Be Created With When Using This Scheme.<br>    Memorymb<br>        The Maximum Amount Of Memory That Vms Will Be Created With When Using This Scheme.<br>    Masterimagevm<br>        The Path Within The Hosting Unit Provider To The Vm Or Snapshot Of Which The Scheme Is Currently Using A Copy.<br>    Masterimagevmdate<br>        The Date And Time That The Copy Of The Vm Image Was Made For The Scheme.<br>    Identitypooluid<br>        The Unique Identifier Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Identitypoolname<br>        The Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Hostingunituid<br>       The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>    Hostingunitname<br>       The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>    Cleanonboot<br>       Indicates Whether The Vms Created Are To Be Reset To A Clean State On Each Boot.<br>    Taskid<br>       The Identifier Of Any Current Task That Is Running For The Provisioning Scheme.

## Notes
If the hosting unit referenced by the provisioning scheme no longer exists (i.e. it has been removed using the Hosting Unit PowerShell snap-in), the provisioning scheme data is deleted from the database without errors. However, the hard disks associated with the provisioning scheme cannot be removed and remain in the hypervisor.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    IllegalParameter<br>    One or more parameters are illegal or are not specified.<br>    ProvisioningSchemeNotFound<br>    The specified provisioning scheme could not be located.<br>    UnableToRemoveProvisioningSchemeDueToAssociatedVM<br>    The provisioning scheme contained VMs and the 'ForgetVM' parameter was not specified.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.<br>    The cmdlet is associated with a task of type DisusedImageCleanUp, and while active will move through the following operations (CurrentOperation field)<br>    Running
## Examples

### Example 1
```
c:\PS>Remove-ProvScheme -ProvisioningSchemeName $provScheme.ProvisioningSchemeName
```
#### Description
Remove the empty provisioning scheme by name.
