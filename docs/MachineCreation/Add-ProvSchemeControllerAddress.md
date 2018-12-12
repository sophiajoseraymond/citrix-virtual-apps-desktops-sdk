
# Add-Provschemecontrolleraddress
Adds a list of host names (as DNS addresses) to a provisioning scheme.
## Syntax
```
Add-ProvSchemeControllerAddress [-ProvisioningSchemeName] <String> [-ControllerAddress] <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Add-ProvSchemeControllerAddress -ProvisioningSchemeUid <Guid> [-ControllerAddress] <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to associate controller hosts (and hence implicitly a set of brokers) with a specific provisioning scheme.  This optional data is passed to the machines created by the Machine Creation Services, where it is used to associate the newly created machine with a broker.  The list is returned along with the provisioning scheme that it is assigned to.


## Related Commands

* [Get-ProvScheme](./Get-ProvScheme/)
* [Remove-ProvSchemeControllerAddress](./Remove-ProvSchemeControllerAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name for the provisioning scheme that the list of addresses is to be added to. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme that the list of addresses is to be added to. | true | false |  |
| ControllerAddress | Specifies the array of DNS names to be added to the provisioning scheme. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Machinecreation.Sdk.Provisioningscheme<br>    You Can Pipe An Object Containing A Parameter Called 'Provisioningschemename' To Add-Provschemecontrolleraddress.

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme<br>   Add-Provschemecontrolleraddress Returns The Updated Provisioningscheme Object Containing The Union Of The Old And New Controller Address Lists.<br>    Provisioningschemeuid &lt;Guid&gt;<br>        The Unique Identifier For The Provisioning Scheme.<br>    Provisioningschemename &lt;String&gt;<br>        The Name Of The Provisioning Scheme.<br>    Cpucount &lt;Int&gt;<br>        The Number Of Processors That Vms Will Be Created With When Using This Scheme.<br>    Memorymb &lt;Int&gt;<br>        The Maximum Amount Of Memory That Vms Will Be Created With When Using This Scheme.<br>    Masterimagevm &lt;String&gt;<br>        The Path Within The Hosting Unit Provider To The Vm Or Snapshot Of Which The Scheme Is Currently Using A Copy.<br>    Masterimagevmdate &lt;Datetime&gt;<br>        The Date And Time That The Copy Of The Vm Image Was Made For The Scheme.<br>    Identitypooluid &lt;Guid&gt;<br>        The Unique Identifier Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Identitypoolname &lt;String&gt;<br>        The Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The Scheme Uses.<br>    Hostingunituid &lt;Guid&gt;<br>       The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Will Use.<br>    Hostingunitname &lt;String&gt;<br>       The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The Scheme Will Use.<br>    Cleanonboot &lt;Boolean&gt;<br>       Indicates Whether Or Not The Vms Created Are To Be Reset To A Clean State On Each Boot.<br>    Taskid &lt;Guid&gt;<br>       The Identifier Of Any Current Task That Is Running For The Provisioning Scheme.<br>    Metadata &lt;Citrix.Machinecreation.Sdk.Metadata\[\]&gt;<br>       The Metadata Associated With This Provisioning Scheme.<br>    Controlleraddress &lt;String\[\]&gt;<br>       The Dns Names Of The Controllers Associated With This Provisioning Scheme For Quick Deploy Purposes.

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    ProvisioningSchemeNotFound<br>    The specified provisioning scheme could not be located.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Add-ProvSchemeControllerAddress -ProvisioningSchemeUid "01a4a008-8ce8-4165-ba9c-cdf15a6b0501" -ControllerAddress (ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com)

ProvisioningSchemeUid  : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

ProvisioningSchemeName : Scheme2

CpuCount               : 1

MemoryMB               : 1024

MasterImageVM          : Base.vm/Base.snapshot

MasterImageVMDate      : 17/05/2010 09:53:40

IdentityPoolUid        : 03743136-e43b-4a87-af74-ab71686b3c16

IdentityPoolName       : idPool1

HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

HostingUnitName        : HostUnit1

CleanOnBoot            : True

TaskId                 : 00000000-0000-0000-0000-000000000000

Metadata               : {}

ControllerAddress      : {ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com}
```
#### Description
Add a set of controllers to the provisioning scheme with the identifier "01a4a008-8ce8-4165-ba9c-cdf15a6b0501".
### Example 2
```
C:\PS>Get-ProvScheme -ProvisioningSchemeName scheme1 | Add-ProvSchemeControllerAddress -ControllerAddress (ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com)

ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42

ProvisioningSchemeName : Scheme1

CpuCount               : 1

MemoryMB               : 1024

MasterImageVM          : Base.vm/Base.snapshot

MasterImageVMDate      : 17/05/2010 09:53:40

IdentityPoolUid        : 03743136-e43b-4a87-af74-ab71686b3c16

IdentityPoolName       : idPool1

HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

HostingUnitName        : HostUnit1

CleanOnBoot            : True

TaskId                 : 00000000-0000-0000-0000-000000000000

Metadata               : {}

ControllerAddress      : {ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com}
```
#### Description
Add controller addresses  to a provisioning scheme using a ProvisioningScheme object.
