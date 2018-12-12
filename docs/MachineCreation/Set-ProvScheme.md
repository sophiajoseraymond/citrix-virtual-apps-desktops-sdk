
# Set-Provscheme
Changes the parameter values for a provisioning scheme.
## Syntax
```
Set-ProvScheme [-ProvisioningSchemeName] <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme [-ProvisioningSchemeName] <String> -IdentityPoolName <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme [-ProvisioningSchemeName] <String> -IdentityPoolUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme -ProvisioningSchemeUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme -ProvisioningSchemeUid <Guid> -IdentityPoolName <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme -ProvisioningSchemeUid <Guid> -IdentityPoolUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to update the parameters of an existing provisioning scheme.

This allows the following parameters to be updated:

Number of CPUs that will be used for VMs created from the provisioning scheme. Maximum amount of memory that will be used for VMs created from the provisioning scheme.

To change the name of the provisioning scheme see Rename-ProvScheme.


## Related Commands

* [New-ProvScheme](./New-ProvScheme/)
* [Remove-ProvScheme](./Remove-ProvScheme/)
* [Get-ProvScheme](./Get-ProvScheme/)
* [Rename-ProvScheme](./Rename-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme to be updated. | true | false |  |
| IdentityPoolName | The name of an identity pool to associate with the provisioning scheme, replacing the present one. | true | false |  |
| IdentityPoolUid | The identifier of an identity pool to associate with the provisioning scheme, replacing the present one. | true | false |  |
| ProvisioningSchemeUid | The identifier of the provisioning scheme to be updated. | true | false |  |
| VMCpuCount | The number of processors that virtual machines created from the provisioning scheme should use. | false | false |  |
| VMMemoryMB | The maximum amount of memory that virtual machines created from the provisioning scheme should use. | false | false |  |
| CustomProperties | The properties of the provisioning scheme that are specific to the target hosting infrastructure. | false | false |  |
| ServiceOffering | The name of the cloud service offering to use when creating machines. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme<br>    This Object Provides Details Of The Provisioning Scheme And Contains The Following Information:<br>    Provisioningschemeuid<br>    Provisioningschemename<br>        The Name Of The Provisioning Scheme.<br>    Cpucount<br>        The Numer Of Processors That Vms Will Be Created With When Using This Scheme.<br>    Memorymb<br>        The Maximum Amount Of Memory That Vms Will Be Created With When Using This Scheme.<br>    Masterimagevm<br>        The Path Within The Hosting Unit Provider To The Vm Or Snapshot Of Which The Scheme Is Currently Using A Copy.<br>    Masterimagevmdate<br>        The Date And Time That The Copy Of The Vm Image Was Made For The Scheme.<br>    Identitypooluid<br>        The Unique Identifier Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Identitypoolname<br>        The Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Hostingunituid<br>       The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>    Hostingunitname<br>       The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>    Cleanonboot<br>       Indicates Whether The Vms Created Are To Be Reset To A Clean State On Each Boot.<br>    Taskid<br>       The Identifier Of Any Current Task That Is Running For The Provisioning Scheme.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    ProvisioningSchemeNotFound<br>    The specified provisioning scheme could not be located.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    HostingUnitNotFound<br>    The hosting unit referenced by the provisioning scheme could not be resolved<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS> Set-ProvScheme -ProvisioningSchemeName MyScheme -VMCpuCount 2
```
#### Description
Updates a provisioning scheme called "MyScheme" to use two processors on the VMs that are created from the provisioning scheme.
