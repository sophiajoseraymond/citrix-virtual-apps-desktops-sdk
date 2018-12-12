
# Rename-Provscheme
Renames a provisioning scheme.
## Syntax
```
Rename-ProvScheme [-ProvisioningSchemeName] <String> [-NewProvisioningSchemeName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Rename-ProvScheme -ProvisioningSchemeUid <Guid> [-NewProvisioningSchemeName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to change the name of an existing provisioning scheme.  The unique identifier for the provisioning scheme never changes after it has been created so, regardless of any name changes, the provisioning scheme can always be identified by its unique identifier.


## Related Commands

* [New-ProvScheme](./New-ProvScheme/)
* [Set-ProvScheme](./Set-ProvScheme/)
* [Get-ProvScheme](./Get-ProvScheme/)
* [Test-ProvSchemeNameAvailable](./Test-ProvSchemeNameAvailable/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The current name of the provisioning scheme. | true | false |  |
| ProvisioningSchemeUid | The identifier for the provisioning scheme that is to be renamed. | true | false |  |
| NewProvisioningSchemeName | The new name for the provisioning scheme.  This must be a name that is not being used by an existing provisioning scheme, and it must not contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | false |  |
| PassThru | Defines whether or not the command returns a result showing the new state of the updated identity pool. | false | false | true |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme<br>    This Object Provides Details Of The Provisioning Scheme And Contains The Following Information:<br>    Provisioningschemeuid<br>        The Unique Identifier For The Provisioning Scheme.<br>    Provisioningschemename<br>        The Name Of The Provisioning Scheme.<br>    Cpucount<br>        The Numer Of Processors That Vms Will Be Created With When Using This Scheme.<br>    Memorymb<br>        The Maximum Amount Of Memory That Vms Will Be Created With When Using This Scheme.<br>    Masterimagevm<br>        The Path Within The Hosting Unit Provider To The Vm Or Snapshot Of Which The Scheme Is Currently Using A Copy.<br>    Masterimagevmdate<br>        The Date And Time That The Copy Of The Vm Image Was Made For The Scheme.<br>    Identitypooluid<br>        The Unique Identifier Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Identitypoolname<br>        The Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Hostingunituid<br>       The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>    Hostingunitname<br>       The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>    Cleanonboot<br>       Indicates Whether The Vms Created Are To Be Reset To A Clean State On Each Boot.<br>    Taskid<br>       The Identifier Of Any Current Task That Is Running For The Provisioning Scheme.<br>    Metadata<br>      The Metadata For The Provisioning Scheme.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    ProvisioningSchemeNotFound<br>    The specified provisioning scheme could not be located.<br>    ProvisioningSchemeNameAlreadyExists<br>    A provisioning scheme with the same name as the new provisioning scheme name already exists.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Rename-ProvScheme -provisioningSchemeName CurrentName -NewProvisioningSchemeName NewName
```
#### Description
Renames a provisioning scheme from "currentName" to "NewName".
### Example 2
```
C:\PS>Rename-ProvScheme -provisioningSchemeName CurrentName -NewProvisioningSchemeName NewName -PassThru

ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42

ProvisioningSchemeName : NewName

CpuCount               : 1

MemoryMB               : 1024

MasterImageVM          : /Base.vm

MasterImageVMDate      : 17/05/2010 08:27:50

IdentityPoolUid        : 03743136-e43b-4a87-af74-ab71686b3c16

IdentityPoolName       : IdPool1

HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

HostingUnitName        : XenHU

CleanOnBoot            : True

TaskId                 :

Metadata               : {}
```
#### Description
Renames a provisioning scheme from "currentName" to "NewName" and displays the resulting state.
